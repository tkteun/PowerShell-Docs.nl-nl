---
title: Voor beeld van RunSpace08-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784687"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="1d953-102">Runspace08-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="1d953-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="1d953-103">Dit is de bron code voor het Runspace08-voor beeld dat wordt beschreven in [een console toepassing maken die para meters toevoegt aan een opdracht](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="1d953-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="1d953-104">Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe, voegt u twee para meters toe aan de tweede opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="1d953-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="1d953-105">De opdrachten die worden toegevoegd aan de pijp lijn zijn de `Get-Process` `Sort-Object` cmdlets en.</span><span class="sxs-lookup"><span data-stu-id="1d953-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1d953-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="1d953-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="1d953-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d953-107">See Also</span></span>

[<span data-ttu-id="1d953-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1d953-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
