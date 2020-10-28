---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Windows PowerShell02
description: Voorbeeld Windows PowerShell02
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657349"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="f9952-103">Voorbeeld Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="f9952-103">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="f9952-104">Dit voor beeld laat zien hoe u opdrachten asynchroon kunt uitvoeren met behulp van de runspaces van een runs Pace-groep.</span><span class="sxs-lookup"><span data-stu-id="f9952-104">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="f9952-105">Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="f9952-105">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9952-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f9952-106">Requirements</span></span>

- <span data-ttu-id="f9952-107">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="f9952-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f9952-108">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="f9952-108">Demonstrates</span></span>

<span data-ttu-id="f9952-109">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="f9952-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f9952-110">Het maken van een RunspacePool-object met het minimum en maximum aantal runspaces dat tegelijkertijd mag worden geopend.</span><span class="sxs-lookup"><span data-stu-id="f9952-110">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="f9952-111">Een lijst met opdrachten maken.</span><span class="sxs-lookup"><span data-stu-id="f9952-111">Creating a list of commands.</span></span>
- <span data-ttu-id="f9952-112">De opdrachten asynchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f9952-112">Running the commands asynchronously.</span></span>
- <span data-ttu-id="f9952-113">De methode [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) aanroepen om te zien hoeveel Runspaces gratis zijn.</span><span class="sxs-lookup"><span data-stu-id="f9952-113">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="f9952-114">Vastleggen van de uitvoer van de opdracht met de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="f9952-114">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="f9952-115">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f9952-115">Example</span></span>

<span data-ttu-id="f9952-116">In dit voor beeld ziet u hoe u de runspaces van een runs Pace-groep opent en hoe u asynchrone opdrachten kunt uitvoeren in deze runspaces.</span><span class="sxs-lookup"><span data-stu-id="f9952-116">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="f9952-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9952-117">See Also</span></span>

[<span data-ttu-id="f9952-118">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="f9952-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
