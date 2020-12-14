---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02-codevoorbeeld (C#)
description: GetProc02-codevoorbeeld (C#)
ms.openlocfilehash: 17fd0d0c0829ed21ef955fd2e62e9ee089d62190
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355609"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="82ff9-103">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="82ff9-103">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="82ff9-104">De volgende code toont de implementatie van een `Get-Process` cmdlet die opdracht regel invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="82ff9-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="82ff9-105">In deze implementatie wordt een `Name` para meter gedefinieerd voor het toestaan van opdracht regel invoer en wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="82ff9-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="82ff9-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="82ff9-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="82ff9-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="82ff9-107">See Also</span></span>

[<span data-ttu-id="82ff9-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82ff9-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
