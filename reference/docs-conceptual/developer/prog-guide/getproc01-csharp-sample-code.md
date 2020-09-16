---
title: GetProc01 (C#) voorbeeld code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778888"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="c8427-102">GetProc01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="c8427-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="c8427-103">De volgende code toont de implementatie van de voor beeld-cmdlet GetProc01.</span><span class="sxs-lookup"><span data-stu-id="c8427-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="c8427-104">U ziet dat de cmdlet wordt vereenvoudigd door de werkelijke hoeveelheid werk van het ophalen van het proces aan de methode [System. Diagnostics. process. GetProcesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) te laten staan.</span><span class="sxs-lookup"><span data-stu-id="c8427-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="c8427-105">U kunt het C#-bron bestand (getproc01.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="c8427-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c8427-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="c8427-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c8427-107">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="c8427-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8427-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c8427-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="c8427-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c8427-109">See Also</span></span>

[<span data-ttu-id="c8427-110">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="c8427-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8427-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8427-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
