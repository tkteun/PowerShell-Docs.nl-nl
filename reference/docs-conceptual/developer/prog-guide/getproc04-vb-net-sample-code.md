---
title: Voorbeeld code voor GetProc04 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416103"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="c5792-102">GetProc04-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c5792-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c5792-103">De volgende code toont de implementatie van een `Get-Process`-cmdlet die niet-afsluit fouten rapporteert.</span><span class="sxs-lookup"><span data-stu-id="c5792-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="c5792-104">Met deze implementatie wordt de methode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) aangeroepen om niet-afsluit fouten te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="c5792-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="c5792-105">U kunt het C# bron bestand (getprov04.cs) voor deze Get-proc-cmdlet downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="c5792-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c5792-106">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="c5792-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c5792-107">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="c5792-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c5792-108">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c5792-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="c5792-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c5792-109">See Also</span></span>

[<span data-ttu-id="c5792-110">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="c5792-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c5792-111">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="c5792-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
