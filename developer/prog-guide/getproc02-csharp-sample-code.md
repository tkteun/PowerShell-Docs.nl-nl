---
title: GetProc02 (C#) voorbeeldcode | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081702"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="782f5-102">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="782f5-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="782f5-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdrachtregel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="782f5-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="782f5-104">U ziet dat deze implementatie definieert een `Name` parameter waarmee het opdrachtregelprogramma invoer en gebruikt de [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) methode als de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="782f5-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="782f5-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="782f5-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="782f5-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="782f5-106">See Also</span></span>

[<span data-ttu-id="782f5-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="782f5-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)