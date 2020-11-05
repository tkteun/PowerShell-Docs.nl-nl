---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02-codevoorbeeld (VB.NET)
description: GetProc02-codevoorbeeld (VB.NET)
ms.openlocfilehash: aefc3a4df5e0f29120916648ecdca41931a4c1c6
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354538"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="f4466-103">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="f4466-103">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="f4466-104">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdracht regel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="f4466-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="f4466-105">In deze implementatie wordt een `Name` para meter gedefinieerd voor het toestaan van opdracht regel invoer en wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f4466-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f4466-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f4466-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="f4466-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f4466-107">See Also</span></span>

[<span data-ttu-id="f4466-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f4466-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
