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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357160"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="ac40b-102">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="ac40b-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="ac40b-103">De volgende code toont de implementatie van een cmdlet `Get-Process` die opdracht regel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="ac40b-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="ac40b-104">U ziet dat deze implementatie een `Name`-para meter definieert om opdracht regel invoer toe te staan en gebruikt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ac40b-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ac40b-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ac40b-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="ac40b-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac40b-106">See Also</span></span>

[<span data-ttu-id="ac40b-107">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="ac40b-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
