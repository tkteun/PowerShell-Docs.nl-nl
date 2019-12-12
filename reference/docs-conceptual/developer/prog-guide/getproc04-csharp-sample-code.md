---
title: GetProc04 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 0ca2ccc5188f0c1784ec14ac204c1fdd624c2e66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416107"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="7d1c8-102">GetProc04-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="7d1c8-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="7d1c8-103">De volgende code toont de implementatie van een `Get-Process`-cmdlet die niet-afsluit fouten rapporteert.</span><span class="sxs-lookup"><span data-stu-id="7d1c8-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="7d1c8-104">Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="7d1c8-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="7d1c8-105">U kunt het C# bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="7d1c8-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7d1c8-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="7d1c8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7d1c8-107">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="7d1c8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7d1c8-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7d1c8-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="7d1c8-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7d1c8-109">See Also</span></span>

[<span data-ttu-id="7d1c8-110">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="7d1c8-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7d1c8-111">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="7d1c8-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
