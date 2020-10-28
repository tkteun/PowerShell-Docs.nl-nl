---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04-codevoorbeeld (C#)
description: GetProc04-codevoorbeeld (C#)
ms.openlocfilehash: 80020b60a7ab34caec0c856b9b7d12021f4276b9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654386"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="145f7-103">GetProc04-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="145f7-103">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="145f7-104">De volgende code toont de implementatie van een `Get-Process` cmdlet die niet-afsluit fouten rapporteert.</span><span class="sxs-lookup"><span data-stu-id="145f7-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="145f7-105">Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="145f7-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="145f7-106">U kunt het C#-bron bestand (getprov04.cs) voor deze Get-Proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="145f7-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="145f7-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="145f7-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="145f7-108">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="145f7-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="145f7-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="145f7-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="145f7-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="145f7-110">See Also</span></span>

[<span data-ttu-id="145f7-111">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="145f7-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="145f7-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="145f7-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
