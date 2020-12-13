---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace05-codevoorbeeld
description: Runspace05-codevoorbeeld
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654204"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="d8e86-103">Runspace05-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="d8e86-103">RunSpace05 Code Sample</span></span>

<span data-ttu-id="d8e86-104">Dit is de bron code voor het Runspace05-voor beeld dat wordt beschreven in [een runs Pace configureren met behulp van RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="d8e86-104">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="d8e86-105">Dit voor beeld laat zien hoe u de runs Pace-configuratie gegevens maakt, een runs Pace maakt, een pijp lijn maakt met één opdracht en vervolgens de pijp lijn uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d8e86-105">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="d8e86-106">De opdracht die wordt uitgevoerd, is de `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8e86-106">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e86-107">U kunt het C#-bron bestand (runspace05.cs) downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="d8e86-107">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d8e86-108">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="d8e86-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d8e86-109">De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map.</span><span class="sxs-lookup"><span data-stu-id="d8e86-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d8e86-110">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="d8e86-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="d8e86-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d8e86-111">See Also</span></span>

[<span data-ttu-id="d8e86-112">Handleiding voor Windows PowerShell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="d8e86-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d8e86-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d8e86-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
