---
title: Voor beeld van RunSpace09-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 2f447fd0ce21c5bca8abe1fddb4e3c7025b70ef1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870575"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="761e2-102">Runspace09-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="761e2-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="761e2-103">Dit is de bron code voor het Runspace09-voor beeld dat wordt beschreven in [een console toepassing maken die een pijp lijn asynchroon aanroept](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="761e2-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="761e2-104">Met deze voorbeeld toepassing wordt een runs Pace gemaakt en geopend, wordt een pijp lijn gemaakt en asynchroon aangeroepen en worden vervolgens pijplijn gebeurtenissen gebruikt om het script asynchroon te verwerken.</span><span class="sxs-lookup"><span data-stu-id="761e2-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="761e2-105">Het script dat door deze toepassing wordt uitgevoerd, maakt de gehele getallen 1 tot en met 10 in intervallen van 0,5 seconden (500 MS).</span><span class="sxs-lookup"><span data-stu-id="761e2-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="761e2-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="761e2-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="761e2-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="761e2-107">See Also</span></span>

[<span data-ttu-id="761e2-108">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="761e2-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
