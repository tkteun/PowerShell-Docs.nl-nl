---
title: GetProc02 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352673"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="a7482-102">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="a7482-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="a7482-103">De volgende code toont de implementatie van een `Get-Process`-cmdlet waarmee invoer van de opdracht regel wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="a7482-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="a7482-104">U ziet dat deze implementatie een `Name` para meter definieert voor het toestaan van opdracht regel invoer en gebruikt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a7482-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a7482-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a7482-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="a7482-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a7482-106">See Also</span></span>

[<span data-ttu-id="a7482-107">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="a7482-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
