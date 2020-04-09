---
title: GetProc02 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: c5e71ddacae1036164c5e8e579ddc8704d30670e
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978386"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="09055-102">GetProc02-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="09055-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="09055-103">De volgende code toont de implementatie van een `Get-Process`-cmdlet waarmee invoer van de opdracht regel wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="09055-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="09055-104">U ziet dat deze implementatie een `Name` para meter definieert voor het toestaan van opdracht regel invoer en gebruikt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) als uitvoer mechanisme voor het verzenden van uitvoer objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="09055-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="09055-105">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="09055-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="09055-106">Zie ook</span><span class="sxs-lookup"><span data-stu-id="09055-106">See Also</span></span>

[<span data-ttu-id="09055-107">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="09055-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
