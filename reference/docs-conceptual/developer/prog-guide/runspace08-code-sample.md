---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace08-codevoorbeeld
description: Runspace08-codevoorbeeld
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654228"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="0a853-103">Runspace08-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="0a853-103">RunSpace08 Code Sample</span></span>

<span data-ttu-id="0a853-104">Dit is de bron code voor het Runspace08-voor beeld dat wordt beschreven in [een console toepassing maken die para meters toevoegt aan een opdracht](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="0a853-104">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="0a853-105">Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe, voegt u twee para meters toe aan de tweede opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="0a853-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="0a853-106">De opdrachten die worden toegevoegd aan de pijp lijn zijn de `Get-Process` `Sort-Object` cmdlets en.</span><span class="sxs-lookup"><span data-stu-id="0a853-106">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0a853-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0a853-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="0a853-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0a853-108">See Also</span></span>

[<span data-ttu-id="0a853-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0a853-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
