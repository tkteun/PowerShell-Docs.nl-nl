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
ms.openlocfilehash: 821d0dd327529614322e446bfb30d128d1b6a7f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081580"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="5a967-102">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="5a967-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5a967-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdrachtregel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="5a967-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="5a967-104">U ziet dat deze implementatie definieert een `Name` parameter waarmee het opdrachtregelprogramma invoer en gebruikt de [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) methode als de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="5a967-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a967-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="5a967-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="5a967-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5a967-106">See Also</span></span>

[<span data-ttu-id="5a967-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a967-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)