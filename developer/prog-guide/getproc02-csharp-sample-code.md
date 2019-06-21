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
ms.openlocfilehash: c4e7c13ffc26980e533530965187df8563003470
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301556"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="6e694-102">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="6e694-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="6e694-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdrachtregel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="6e694-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="6e694-104">U ziet dat deze implementatie definieert een `Name` parameter waarmee het opdrachtregelprogramma invoer en gebruikt de [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) methode als de uitvoer-mechanisme voor het verzenden van uitvoer objecten naar de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="6e694-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6e694-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="6e694-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="6e694-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6e694-106">See Also</span></span>

[<span data-ttu-id="6e694-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6e694-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
