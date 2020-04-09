---
title: Voor beeld van Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978641"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="f2cce-102">Voorbeeld Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="f2cce-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="f2cce-103">Dit voor beeld laat zien hoe u opdrachten asynchroon kunt uitvoeren met behulp van de runspaces van een runs Pace-groep.</span><span class="sxs-lookup"><span data-stu-id="f2cce-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="f2cce-104">Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="f2cce-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2cce-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f2cce-105">Requirements</span></span>

- <span data-ttu-id="f2cce-106">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="f2cce-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f2cce-107">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="f2cce-107">Demonstrates</span></span>

<span data-ttu-id="f2cce-108">In dit voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="f2cce-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="f2cce-109">Het maken van een RunspacePool-object met het minimum en maximum aantal runspaces dat tegelijkertijd mag worden geopend.</span><span class="sxs-lookup"><span data-stu-id="f2cce-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="f2cce-110">Een lijst met opdrachten maken.</span><span class="sxs-lookup"><span data-stu-id="f2cce-110">Creating a list of commands.</span></span>
- <span data-ttu-id="f2cce-111">De opdrachten asynchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f2cce-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="f2cce-112">De methode [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) aanroepen om te zien hoeveel Runspaces gratis zijn.</span><span class="sxs-lookup"><span data-stu-id="f2cce-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="f2cce-113">Vastleggen van de uitvoer van de opdracht met de methode [System. Management. Automation. Power shell. Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="f2cce-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="f2cce-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f2cce-114">Example</span></span>

<span data-ttu-id="f2cce-115">In dit voor beeld ziet u hoe u de runspaces van een runs Pace-groep opent en hoe u asynchrone opdrachten kunt uitvoeren in deze runspaces.</span><span class="sxs-lookup"><span data-stu-id="f2cce-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="f2cce-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f2cce-116">See Also</span></span>

[<span data-ttu-id="f2cce-117">Een Windows Power shell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="f2cce-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
