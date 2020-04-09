---
title: GetProc01 (C#) voorbeeld code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 71ba68521ed8d26d0c85169d2b0d547cc6d2d5e3
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978420"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="14c87-102">GetProc01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="14c87-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="14c87-103">De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01.</span><span class="sxs-lookup"><span data-stu-id="14c87-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="14c87-104">U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.</span><span class="sxs-lookup"><span data-stu-id="14c87-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="14c87-105">U kunt het C# bron bestand (getproc01.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="14c87-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="14c87-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="14c87-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="14c87-107">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="14c87-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="14c87-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="14c87-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="14c87-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="14c87-109">See Also</span></span>

[<span data-ttu-id="14c87-110">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="14c87-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="14c87-111">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="14c87-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
