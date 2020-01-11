---
title: Voor beeld van RunSpace05-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 8802e308712be93992ead5ef77b97d8c21b137f7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870639"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="38722-102">Runspace05-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="38722-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="38722-103">Dit is de bron code voor het Runspace05-voor beeld dat wordt beschreven in [een runs Pace configureren met behulp van RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="38722-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="38722-104">Dit voor beeld laat zien hoe u de runs Pace-configuratie gegevens maakt, een runs Pace maakt, een pijp lijn maakt met één opdracht en vervolgens de pijp lijn uitvoert.</span><span class="sxs-lookup"><span data-stu-id="38722-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="38722-105">De opdracht die wordt uitgevoerd, is de `Get-Process`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="38722-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="38722-106">U kunt het C# bron bestand (runspace05.cs) downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="38722-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="38722-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="38722-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="38722-108">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="38722-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="38722-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="38722-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="38722-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="38722-110">See Also</span></span>

[<span data-ttu-id="38722-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="38722-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="38722-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="38722-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
