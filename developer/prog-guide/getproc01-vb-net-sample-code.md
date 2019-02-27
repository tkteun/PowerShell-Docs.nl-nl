---
title: GetProc01 voorbeeldcode (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846856"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="07b35-102">GetProc01-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="07b35-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="07b35-103">De volgende code toont de uitvoering van de GetProc01 voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07b35-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="07b35-104">U ziet dat de cmdlet wordt vereenvoudigd door over te laten het eigenlijke werk van het ophalen van proces aan de [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) methode.</span><span class="sxs-lookup"><span data-stu-id="07b35-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="07b35-105">U kunt downloaden de C# bronbestand (getproc01.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="07b35-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="07b35-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="07b35-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="07b35-107">U kunt downloaden de C# bronbestand (getproc01.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="07b35-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="07b35-108">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="07b35-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="07b35-109">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="07b35-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="07b35-110">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="07b35-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="07b35-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07b35-111">See Also</span></span>

[<span data-ttu-id="07b35-112">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="07b35-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="07b35-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="07b35-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)