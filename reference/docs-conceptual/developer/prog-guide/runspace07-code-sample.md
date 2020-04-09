---
title: Voor beeld van RunSpace07-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 55005a254ef50a2230121095770899cb3b9b70f1
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978218"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="50c93-102">Runspace07-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="50c93-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="50c93-103">Dit is de bron code voor het Runspace07-voor beeld dat wordt beschreven in [een console toepassing maken waarmee opdrachten worden toegevoegd aan een pijp lijn](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="50c93-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="50c93-104">Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="50c93-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="50c93-105">De opdrachten die zijn toegevoegd aan de pijp lijn zijn de `Get-Process` en `Measure-Object`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="50c93-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="50c93-106">U kunt het C# bron bestand (runspace07.cs) downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="50c93-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="50c93-107">Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.</span><span class="sxs-lookup"><span data-stu-id="50c93-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="50c93-108">De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.</span><span class="sxs-lookup"><span data-stu-id="50c93-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="50c93-109">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="50c93-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="50c93-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="50c93-110">See Also</span></span>

[<span data-ttu-id="50c93-111">Hand leiding voor Windows Power shell-programmeurs</span><span class="sxs-lookup"><span data-stu-id="50c93-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="50c93-112">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="50c93-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
