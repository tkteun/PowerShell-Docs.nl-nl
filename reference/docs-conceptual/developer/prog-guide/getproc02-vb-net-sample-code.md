---
title: Voorbeeld code voor GetProc02 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357160"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="a1e89-102">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="a1e89-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="a1e89-103">De volgende code toont de implementatie van een `Get-Process`-cmdlet waarmee invoer van de opdracht regel wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="a1e89-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="a1e89-104">U ziet dat deze implementatie een `Name` para meter definieert voor het toestaan van opdracht regel invoer en gebruikt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="a1e89-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a1e89-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="a1e89-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="a1e89-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a1e89-106">See Also</span></span>

[<span data-ttu-id="a1e89-107">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="a1e89-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
