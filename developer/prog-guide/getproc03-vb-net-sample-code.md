---
title: GetProc03 voorbeeldcode (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301560"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="610e8-102">GetProc03-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="610e8-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="610e8-103">De volgende code toont de implementatie van een `Get-Process` cmdlet kan accepteren pipelined invoer.</span><span class="sxs-lookup"><span data-stu-id="610e8-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="610e8-104">Deze implementatie definieert een `Name` parameter die de invoer van de pijplijn, accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en gebruikt vervolgens de [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)methode als de uitvoer-mechanisme voor het verzenden van objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="610e8-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="610e8-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="610e8-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
