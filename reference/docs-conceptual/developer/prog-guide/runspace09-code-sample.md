---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace09-codevoorbeeld
description: Runspace09-codevoorbeeld
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654193"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="5e661-103">Runspace09-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="5e661-103">RunSpace09 Code Sample</span></span>

<span data-ttu-id="5e661-104">Dit is de bron code voor het Runspace09-voor beeld dat wordt beschreven in [een console toepassing maken die een pijp lijn asynchroon aanroept](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="5e661-104">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="5e661-105">Met deze voorbeeld toepassing wordt een runs Pace gemaakt en geopend, wordt een pijp lijn gemaakt en asynchroon aangeroepen en worden vervolgens pijplijn gebeurtenissen gebruikt om het script asynchroon te verwerken.</span><span class="sxs-lookup"><span data-stu-id="5e661-105">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="5e661-106">Het script dat door deze toepassing wordt uitgevoerd, maakt de gehele getallen 1 tot en met 10 in intervallen van 0,5 seconden (500 MS).</span><span class="sxs-lookup"><span data-stu-id="5e661-106">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="5e661-107">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5e661-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="5e661-108">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5e661-108">See Also</span></span>

[<span data-ttu-id="5e661-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5e661-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
