---
title: GetProc04 (C#) voorbeeldcode | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 936fb355be40b98136719ea929cf50b06705b687
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081628"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="18f63-102">GetProc04-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="18f63-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="18f63-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die afsluitfouten-rapporten.</span><span class="sxs-lookup"><span data-stu-id="18f63-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="18f63-104">Deze implementatie roept de [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode voor het rapport afsluitfouten.</span><span class="sxs-lookup"><span data-stu-id="18f63-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="18f63-105">U kunt downloaden de C# bronbestand (getprov04.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="18f63-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="18f63-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="18f63-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="18f63-107">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="18f63-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="18f63-108">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="18f63-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="18f63-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="18f63-109">See Also</span></span>

[<span data-ttu-id="18f63-110">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="18f63-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="18f63-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="18f63-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)