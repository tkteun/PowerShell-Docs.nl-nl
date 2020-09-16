---
title: GetProc02 (C#) voorbeeld code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d9afa8fff23d99661987c067e8082a9294c12717
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787152"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="e2b55-102">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="e2b55-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="e2b55-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdracht regel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="e2b55-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="e2b55-104">In deze implementatie wordt een `Name` para meter gedefinieerd voor het toestaan van opdracht regel invoer en wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e2b55-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e2b55-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e2b55-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="e2b55-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e2b55-106">See Also</span></span>

[<span data-ttu-id="e2b55-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e2b55-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
