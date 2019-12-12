---
title: Voor beeld van RunSpace08-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356957"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="3095a-102">Runspace08-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="3095a-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="3095a-103">Dit is de bron code voor het Runspace08-voor beeld dat wordt beschreven in [een console toepassing maken die para meters toevoegt aan een opdracht](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="3095a-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="3095a-104">Met deze voorbeeld toepassing maakt u een runs Pace, maakt u een pijp lijn, voegt u twee opdrachten aan de pijp lijn toe, voegt u twee para meters toe aan de tweede opdracht en voert u de pijp lijn uit.</span><span class="sxs-lookup"><span data-stu-id="3095a-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="3095a-105">De opdrachten die worden toegevoegd aan de pijp lijn zijn de `Get-Process` en `Sort-Object`-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3095a-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3095a-106">Code voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3095a-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="3095a-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3095a-107">See Also</span></span>

[<span data-ttu-id="3095a-108">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="3095a-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
