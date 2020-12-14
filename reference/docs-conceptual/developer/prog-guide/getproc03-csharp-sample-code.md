---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03-codevoorbeeld (C#)
description: GetProc03-codevoorbeeld (C#)
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355575"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="3feeb-103">GetProc03-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="3feeb-103">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="3feeb-104">De volgende code toont de implementatie van een `Get-Process` cmdlet die de invoer van een pijp lijn kan accepteren.</span><span class="sxs-lookup"><span data-stu-id="3feeb-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="3feeb-105">Met deze implementatie wordt een `Name` para meter gedefinieerd die de invoer van de pijp lijn accepteert, worden proces gegevens van de lokale computer opgehaald op basis van de opgegeven namen. vervolgens wordt de methode [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) gebruikt als uitvoer mechanisme voor het verzenden van objecten naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="3feeb-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="3feeb-106">U kunt het C#-bron bestand (getprov03.cs) voor deze Get-Proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="3feeb-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3feeb-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="3feeb-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="3feeb-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="3feeb-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3feeb-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3feeb-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="3feeb-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3feeb-110">See Also</span></span>

[<span data-ttu-id="3feeb-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="3feeb-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3feeb-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3feeb-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
