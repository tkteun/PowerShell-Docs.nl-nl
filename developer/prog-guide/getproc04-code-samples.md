---
title: GetProc04 codevoorbeelden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846422"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="1ab07-102">GetProc04-codevoorbeelden</span><span class="sxs-lookup"><span data-stu-id="1ab07-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="1ab07-103">Hier volgen de codevoorbeelden voor de GetProc04 voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1ab07-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="1ab07-104">Dit is de `Get-Process` cmdlet-voorbeeld wordt beschreven in [toe te voegen Nonterminating foutrapportage aan uw Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="1ab07-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="1ab07-105">Dit `Get-Process` aanroepen van cmdlet de [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode wanneer er een ongeldige bewerking-uitzondering is opgetreden tijdens het ophalen van gegevens voor proces.</span><span class="sxs-lookup"><span data-stu-id="1ab07-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="1ab07-106">U kunt downloaden de C# bronbestand (getprov04.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="1ab07-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1ab07-107">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1ab07-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="1ab07-108">U kunt downloaden de C# bronbestand (getprov04.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="1ab07-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1ab07-109">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1ab07-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1ab07-110">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="1ab07-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="1ab07-111">Volledig voorbeeld van code, Zie de volgende onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="1ab07-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="1ab07-112">Language</span><span class="sxs-lookup"><span data-stu-id="1ab07-112">Language</span></span>|<span data-ttu-id="1ab07-113">Onderwerp</span><span class="sxs-lookup"><span data-stu-id="1ab07-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="1ab07-114">C#</span><span class="sxs-lookup"><span data-stu-id="1ab07-114">C#</span></span>|[<span data-ttu-id="1ab07-115">GetProc04 (C#) voorbeeldcode</span><span class="sxs-lookup"><span data-stu-id="1ab07-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="1ab07-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="1ab07-116">VB.NET</span></span>|[<span data-ttu-id="1ab07-117">GetProc04 voorbeeldcode (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="1ab07-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="1ab07-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1ab07-118">See Also</span></span>

[<span data-ttu-id="1ab07-119">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="1ab07-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1ab07-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1ab07-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)