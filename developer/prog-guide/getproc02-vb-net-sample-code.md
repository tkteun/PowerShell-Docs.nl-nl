---
title: GetProc02 voorbeeldcode (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301337"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="51930-102">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="51930-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="51930-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdrachtregel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="51930-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="51930-104">U ziet dat deze implementatie definieert een `Name` parameter waarmee het opdrachtregelprogramma invoer en gebruikt de [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) methode als de uitvoer-mechanisme voor het verzenden van uitvoer objecten naar de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="51930-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="51930-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="51930-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="51930-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="51930-106">See Also</span></span>

[<span data-ttu-id="51930-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="51930-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
