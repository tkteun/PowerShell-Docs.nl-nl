---
title: Codevoorbeeld RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 1a09cfee3bb317de6c1ca4dde86a87d72a498e6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081271"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="78632-102">Runspace08-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="78632-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="78632-103">Hier volgt de broncode voor het voorbeeld Runspace08 die zijn beschreven [het maken van een toepassing die wordt toegevoegd Consoleparameters aan een opdracht](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span><span class="sxs-lookup"><span data-stu-id="78632-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="78632-104">Deze voorbeeldtoepassing maakt een runspace, wordt een pijplijn gemaakt, worden twee opdrachten toegevoegd aan de pijplijn, voegt u twee parameters toe aan de tweede opdracht en voert de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="78632-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="78632-105">De opdrachten die worden toegevoegd aan de pijplijn zijn de `Get-Process` en `Sort-Object` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="78632-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="78632-106">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="78632-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="78632-107">Zie ook</span><span class="sxs-lookup"><span data-stu-id="78632-107">See Also</span></span>

[<span data-ttu-id="78632-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78632-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)