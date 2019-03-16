---
title: Voorbeelden van Cmdlet-Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056256"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="80e78-102">Voorbeelden van cmdlet-code</span><span class="sxs-lookup"><span data-stu-id="80e78-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="80e78-103">In deze sectie bevat voorbeelden van de cmdlet-code die u gebruiken kunt om te beginnen met het schrijven van uw eigen cmdlets.</span><span class="sxs-lookup"><span data-stu-id="80e78-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80e78-104">Als u wilt dat Stapsgewijze instructies voor het schrijven van cmdlets, raadpleegt u [zelfstudies voor het schrijven van Cmdlets](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="80e78-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="80e78-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="80e78-105">In This Section</span></span>

<span data-ttu-id="80e78-106">[Over het schrijven van een eenvoudige Cmdlet](./how-to-write-a-simple-cmdlet.md) in dit voorbeeld ziet u de basisstructuur van de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="80e78-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="80e78-107">[Hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md) in dit voorbeeld laat zien hoe de verschillende typen parameters declareren.</span><span class="sxs-lookup"><span data-stu-id="80e78-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="80e78-108">[Hoe parametersets declareren](./how-to-declare-parameter-sets.md) in dit voorbeeld laat zien hoe om te declareren van sets met parameters die de actie uitvoert voor een cmdlet kunnen wijzigen.</span><span class="sxs-lookup"><span data-stu-id="80e78-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="80e78-109">[Hoe u Parameter invoer valideren](./how-to-validate-parameter-input.md) deze voorbeelden laten zien hoe u voor het valideren van de parameter-invoer.</span><span class="sxs-lookup"><span data-stu-id="80e78-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="80e78-110">[Hoe u dynamische Parameters declareren](./how-to-declare-dynamic-parameters.md) in dit voorbeeld laat zien hoe een parameter die is toegevoegd tijdens runtime declareren.</span><span class="sxs-lookup"><span data-stu-id="80e78-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="80e78-111">[Hoe kunt u Scripts aanroepen vanuit een Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) in dit voorbeeld laat zien hoe u een script dat wordt doorgegeven aan een cmdlet aanroepen.</span><span class="sxs-lookup"><span data-stu-id="80e78-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="80e78-112">[Het onderdrukken van invoer verwerkingsmethoden](./how-to-override-input-processing-methods.md) deze voorbeelden ziet u de basisstructuur gebruikt voor het overschrijven van de methoden BeginProcessing ProcessRecord en EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="80e78-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="80e78-113">[Hoe u ondersteuningsaanvragen shouldprocess wordt overgeslagen](./how-to-request-confirmations.md) dit voorbeeld laat zien hoe de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden moeten worden aangeroepen vanuit een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80e78-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="80e78-114">[Hoe u ondersteuning voor transacties](./how-to-support-transactions.md) dit voorbeeld laat zien hoe u om aan te geven dat de cmdlet biedt ondersteuning voor transacties en het implementeren van de actie die moet worden uitgevoerd wanneer de cmdlet wordt gebruikt binnen een transactie.</span><span class="sxs-lookup"><span data-stu-id="80e78-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="80e78-115">[Hoe u taken ondersteunen](./how-to-support-jobs.md) in dit voorbeeld laat zien hoe ter ondersteuning van taken bij het schrijven van cmdlets.</span><span class="sxs-lookup"><span data-stu-id="80e78-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="80e78-116">[Het aanroepen van een Cmdlet uit binnen een Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) dit voorbeeld wordt het aanroepen van een cmdlet uit binnen een andere cmdlet, zodat u kunt de functionaliteit van de cmdlet aangeroepen toevoegen aan de cmdlet die u ontwikkelt.</span><span class="sxs-lookup"><span data-stu-id="80e78-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="80e78-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="80e78-117">See Also</span></span>

[<span data-ttu-id="80e78-118">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80e78-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
