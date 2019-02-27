---
title: Codevoorbeeld RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 95b25746a8e99deb871905734700aba51cd7765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845834"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="f6db6-102">Runspace10-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="f6db6-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="f6db6-103">Hier volgt de broncode voor het voorbeeld Runspace10.</span><span class="sxs-lookup"><span data-stu-id="f6db6-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="f6db6-104">Deze voorbeeldtoepassing wordt toegevoegd een cmdlet voor het [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) en gebruikt vervolgens de gewijzigde configuratie-informatie voor het maken van de runspace.</span><span class="sxs-lookup"><span data-stu-id="f6db6-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="f6db6-105">U kunt downloaden de C# bronbestand (runspace10.cs) met behulp van Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="f6db6-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f6db6-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f6db6-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f6db6-107">U kunt downloaden de C# bronbestand (runspace10.cs) met behulp van Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="f6db6-107">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f6db6-108">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="f6db6-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f6db6-109">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="f6db6-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f6db6-110">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="f6db6-110">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="f6db6-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6db6-111">See Also</span></span>

[<span data-ttu-id="f6db6-112">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="f6db6-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f6db6-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f6db6-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)