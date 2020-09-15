---
title: GetProc04 (C#) voorbeeld code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: dd3965ee504641b1b629ba203090ee14c670da43
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771886"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="4b90d-102">GetProc04-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="4b90d-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="4b90d-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die niet-afsluit fouten rapporteert.</span><span class="sxs-lookup"><span data-stu-id="4b90d-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="4b90d-104">Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="4b90d-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="4b90d-105">U kunt het C#-bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="4b90d-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4b90d-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="4b90d-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4b90d-107">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="4b90d-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4b90d-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="4b90d-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs" range="11-98":::

## <a name="see-also"></a><span data-ttu-id="4b90d-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4b90d-109">See Also</span></span>

[<span data-ttu-id="4b90d-110">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="4b90d-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4b90d-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4b90d-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
