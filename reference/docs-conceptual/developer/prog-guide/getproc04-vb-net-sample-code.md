---
title: Voorbeeld code voor GetProc04 (VB.NET) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63fbbb2d6bef4634bf72d4b0f9e429de9ed9deca
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771869"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="fca6a-102">GetProc04-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="fca6a-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="fca6a-103">De volgende code toont de implementatie van een `Get-Process` cmdlet die niet-afsluit fouten rapporteert.</span><span class="sxs-lookup"><span data-stu-id="fca6a-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="fca6a-104">Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="fca6a-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="fca6a-105">U kunt het C#-bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="fca6a-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fca6a-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="fca6a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="fca6a-107">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="fca6a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fca6a-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="fca6a-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="fca6a-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fca6a-109">See Also</span></span>

[<span data-ttu-id="fca6a-110">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="fca6a-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fca6a-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fca6a-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
