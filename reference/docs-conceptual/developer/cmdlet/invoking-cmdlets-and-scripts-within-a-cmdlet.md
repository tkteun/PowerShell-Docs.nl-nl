---
title: Cmdlets en scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d5f76242c02763c41b81215bbb031e19869066a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786574"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="fcede-102">Cmdlets en scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="fcede-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="fcede-103">Met een cmdlet kunnen andere cmdlets en scripts worden aangeroepen in de invoer verwerkings methode van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcede-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="fcede-104">Hierdoor kunt u de functionaliteit van bestaande cmdlets en scripts toevoegen aan uw cmdlet zonder dat u de code opnieuw hoeft te schrijven.</span><span class="sxs-lookup"><span data-stu-id="fcede-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="fcede-105">De methode Invoke</span><span class="sxs-lookup"><span data-stu-id="fcede-105">The Invoke Method</span></span>

<span data-ttu-id="fcede-106">Alle cmdlets kunnen een bestaande cmdlet aanroepen door het aanroepen van de methode [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) vanuit een invoer verwerkings methode, zoals [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), die wordt overschreven door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcede-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="fcede-107">U kunt echter alleen de cmdlets aanroepen die rechtstreeks zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="fcede-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="fcede-108">U kunt geen cmdlet aanroepen die is afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="fcede-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="fcede-109">De methode [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) heeft de volgende varianten.</span><span class="sxs-lookup"><span data-stu-id="fcede-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="fcede-110">[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een verzameling van type-objecten geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fcede-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="fcede-111">[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een sterk getypeerde emumerator geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fcede-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="fcede-112">Met deze variant kan de gebruiker de objecten in de verzameling gebruiken om aangepaste bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="fcede-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="fcede-113">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="fcede-113">Examples</span></span>

|<span data-ttu-id="fcede-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fcede-114">Example</span></span>|<span data-ttu-id="fcede-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fcede-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcede-116">Cmdlets aanroepen binnen een cmdlet</span><span class="sxs-lookup"><span data-stu-id="fcede-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="fcede-117">In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcede-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="fcede-118">Scripts aanroepen binnen een cmdlet</span><span class="sxs-lookup"><span data-stu-id="fcede-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="fcede-119">In dit voor beeld ziet u hoe u een script aanroept dat bij de cmdlet wordt geleverd vanuit een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fcede-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fcede-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fcede-120">See Also</span></span>

[<span data-ttu-id="fcede-121">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="fcede-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
