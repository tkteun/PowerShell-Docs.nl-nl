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
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977536"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="73fa0-102">Runspace09-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="73fa0-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="73fa0-103">Dit is de bron code voor het Runspace09-voor beeld dat wordt beschreven in [een console toepassing maken die een pijp lijn asynchroon aanroept](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span><span class="sxs-lookup"><span data-stu-id="73fa0-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="73fa0-104">Met deze voorbeeld toepassing wordt een runs Pace gemaakt en geopend, wordt een pijp lijn gemaakt en asynchroon aangeroepen en worden vervolgens pijplijn gebeurtenissen gebruikt om het script asynchroon te verwerken.</span><span class="sxs-lookup"><span data-stu-id="73fa0-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="73fa0-105">Het script dat door deze toepassing wordt uitgevoerd, maakt de gehele getallen 1 tot en met 10 in intervallen van 0,5 seconden (500 MS).</span><span class="sxs-lookup"><span data-stu-id="73fa0-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="73fa0-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="73fa0-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="73fa0-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73fa0-107">See Also</span></span>

[<span data-ttu-id="73fa0-108">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="73fa0-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
