---
title: Voorbeeld van de Windows-PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082512"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="71a4d-102">Voorbeeld Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="71a4d-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="71a4d-103">In dit voorbeeld laat zien hoe opdrachten asynchroon uitvoeren met behulp van de runspaces van een groep runspace.</span><span class="sxs-lookup"><span data-stu-id="71a4d-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="71a4d-104">Het voorbeeld genereert een lijst met opdrachten en vervolgens deze opdrachten worden uitgevoerd terwijl de Windows PowerShell-engine wordt een runspace geopend uit de pool wanneer dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="71a4d-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="71a4d-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="71a4d-105">Requirements</span></span>

- <span data-ttu-id="71a4d-106">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="71a4d-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="71a4d-107">Ziet u</span><span class="sxs-lookup"><span data-stu-id="71a4d-107">Demonstrates</span></span>

<span data-ttu-id="71a4d-108">In dit voorbeeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="71a4d-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="71a4d-109">Het maken van een object RunspacePool met een minimum en maximum aantal runspaces kunnen worden geopend op hetzelfde moment.</span><span class="sxs-lookup"><span data-stu-id="71a4d-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="71a4d-110">Het maken van een lijst met opdrachten.</span><span class="sxs-lookup"><span data-stu-id="71a4d-110">Creating a list of commands.</span></span>

- <span data-ttu-id="71a4d-111">De opdrachten asynchroon uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="71a4d-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="71a4d-112">Aanroepen van de [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) methode om te zien hoeveel runspaces zijn gratis.</span><span class="sxs-lookup"><span data-stu-id="71a4d-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="71a4d-113">Vastleggen van de uitvoer van de opdracht met de [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.</span><span class="sxs-lookup"><span data-stu-id="71a4d-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="71a4d-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="71a4d-114">Example</span></span>

<span data-ttu-id="71a4d-115">Dit voorbeeld laat zien hoe u opent de runspaces van een groep runspace en asynchroon uitvoeren van opdrachten in deze runspaces genoemd.</span><span class="sxs-lookup"><span data-stu-id="71a4d-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="71a4d-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="71a4d-116">See Also</span></span>

[<span data-ttu-id="71a4d-117">Een Windows PowerShell-hosttoepassing schrijven</span><span class="sxs-lookup"><span data-stu-id="71a4d-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)