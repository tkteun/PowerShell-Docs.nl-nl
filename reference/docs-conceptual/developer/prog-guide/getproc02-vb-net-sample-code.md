---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02-codevoorbeeld (VB.NET)
description: GetProc02-codevoorbeeld (VB.NET)
ms.openlocfilehash: e13da4689b7f4ba4878e83cd826076a6394d9fb2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654360"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="6763b-103">GetProc02-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6763b-103">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6763b-104">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdracht regel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="6763b-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="6763b-105">In deze implementatie wordt een `Name` para meter gedefinieerd voor het toestaan van opdracht regel invoer en wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="6763b-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6763b-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6763b-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="6763b-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6763b-107">See Also</span></span>

[<span data-ttu-id="6763b-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6763b-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
