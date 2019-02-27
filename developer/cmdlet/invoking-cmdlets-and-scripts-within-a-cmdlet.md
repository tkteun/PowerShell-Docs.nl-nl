---
title: Aanroepen van de Cmdlets en -Scripts in een Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846240"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="274cc-102">Cmdlets en scripts in een cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="274cc-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="274cc-103">Een cmdlet kunt aanroepen andere cmdlets en -scripts uit binnen de invoer-methode van de cmdlet verwerkt.</span><span class="sxs-lookup"><span data-stu-id="274cc-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="274cc-104">Hiermee kunt u de functionaliteit van bestaande cmdlets en -scripts toevoegen aan uw cmdlet zonder de code te herschrijven.</span><span class="sxs-lookup"><span data-stu-id="274cc-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="274cc-105">De methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="274cc-105">The Invoke Method</span></span>

<span data-ttu-id="274cc-106">Alle cmdlets kan aanroepen van een bestaande cmdlet door het aanroepen van de [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) methode uit binnen een invoer verwerken methode, zoals [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), dat wil zeggen overschreven door de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="274cc-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="274cc-107">Echter, kunt u alleen die cmdlets die zijn afgeleid rechtstreeks van aanroepen de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="274cc-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="274cc-108">U kunt geen aanroepen een cmdlet die is afgeleid van de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.</span><span class="sxs-lookup"><span data-stu-id="274cc-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="274cc-109">De [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) methode heeft de volgende varianten.</span><span class="sxs-lookup"><span data-stu-id="274cc-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="274cc-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) deze variant roept de cmdlet-object en retourneert een verzameling van objecten van het type "T".</span><span class="sxs-lookup"><span data-stu-id="274cc-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="274cc-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) deze variant roept de cmdlet-object en geeft als resultaat een sterk getypeerde emumerator.</span><span class="sxs-lookup"><span data-stu-id="274cc-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="274cc-112">Deze variant kan de gebruiker de objecten te gebruiken in de verzameling aangepaste bewerkingen uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="274cc-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="274cc-113">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="274cc-113">Examples</span></span>

|<span data-ttu-id="274cc-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="274cc-114">Example</span></span>|<span data-ttu-id="274cc-115">Description</span><span class="sxs-lookup"><span data-stu-id="274cc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="274cc-116">Cmdlets binnen een Cmdlet aanroepen</span><span class="sxs-lookup"><span data-stu-id="274cc-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="274cc-117">In dit voorbeeld laat zien hoe een cmdlet uit binnen een andere cmdlet aanroepen.</span><span class="sxs-lookup"><span data-stu-id="274cc-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="274cc-118">Aanroepen van Scripts in een Cmdlet</span><span class="sxs-lookup"><span data-stu-id="274cc-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="274cc-119">In dit voorbeeld laat zien hoe een script dat wordt doorgegeven aan de cmdlet uit binnen een andere cmdlet aanroepen.</span><span class="sxs-lookup"><span data-stu-id="274cc-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="274cc-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="274cc-120">See Also</span></span>

[<span data-ttu-id="274cc-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="274cc-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
