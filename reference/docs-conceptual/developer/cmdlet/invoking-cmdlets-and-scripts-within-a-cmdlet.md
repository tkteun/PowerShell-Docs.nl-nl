---
title: Cmdlets en scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355424"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="ec7f0-102">Cmdlets en scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="ec7f0-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="ec7f0-103">Met een cmdlet kunnen andere cmdlets en scripts worden aangeroepen in de invoer verwerkings methode van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="ec7f0-104">Hierdoor kunt u de functionaliteit van bestaande cmdlets en scripts toevoegen aan uw cmdlet zonder dat u de code opnieuw hoeft te schrijven.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="ec7f0-105">De methode Invoke</span><span class="sxs-lookup"><span data-stu-id="ec7f0-105">The Invoke Method</span></span>

<span data-ttu-id="ec7f0-106">Alle cmdlets kunnen een bestaande cmdlet aanroepen door het aanroepen van de methode [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) vanuit een invoer verwerkings methode, zoals [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), die wordt overschreven door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="ec7f0-107">U kunt echter alleen de cmdlets aanroepen die rechtstreeks zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="ec7f0-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="ec7f0-108">U kunt geen cmdlet aanroepen die is afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="ec7f0-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="ec7f0-109">De methode [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) heeft de volgende varianten.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="ec7f0-110">[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een verzameling van type-objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="ec7f0-111">[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een sterk getypeerde emumerator geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="ec7f0-112">Met deze variant kan de gebruiker de objecten in de verzameling gebruiken om aangepaste bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="ec7f0-113">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="ec7f0-113">Examples</span></span>

|<span data-ttu-id="ec7f0-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ec7f0-114">Example</span></span>|<span data-ttu-id="ec7f0-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ec7f0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec7f0-116">Cmdlets aanroepen binnen een cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec7f0-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="ec7f0-117">In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="ec7f0-118">Scripts aanroepen binnen een cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec7f0-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="ec7f0-119">In dit voor beeld ziet u hoe u een script aanroept dat bij de cmdlet wordt geleverd vanuit een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec7f0-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ec7f0-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ec7f0-120">See Also</span></span>

[<span data-ttu-id="ec7f0-121">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="ec7f0-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
