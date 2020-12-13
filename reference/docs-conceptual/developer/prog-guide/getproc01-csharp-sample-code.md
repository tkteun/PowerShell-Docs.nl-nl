---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01-codevoorbeeld (C#)
description: GetProc01-codevoorbeeld (C#)
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654478"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="5b0fd-103">GetProc01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="5b0fd-103">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="5b0fd-104">De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01.</span><span class="sxs-lookup"><span data-stu-id="5b0fd-104">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="5b0fd-105">U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.</span><span class="sxs-lookup"><span data-stu-id="5b0fd-105">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="5b0fd-106">U kunt het C#-bron bestand (getproc01.cs) voor deze Get-Proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="5b0fd-106">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5b0fd-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="5b0fd-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5b0fd-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="5b0fd-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5b0fd-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5b0fd-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="5b0fd-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5b0fd-110">See Also</span></span>

[<span data-ttu-id="5b0fd-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="5b0fd-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5b0fd-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5b0fd-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
