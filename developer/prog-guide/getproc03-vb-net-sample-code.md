---
title: GetProc03 voorbeeldcode (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058246"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="9ad21-102">GetProc03-codevoorbeeld (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="9ad21-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="9ad21-103">De volgende code toont de implementatie van een `Get-Process` cmdlet kan accepteren pipelined invoer.</span><span class="sxs-lookup"><span data-stu-id="9ad21-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="9ad21-104">Deze implementatie definieert een `Name` parameter die de invoer van de pijplijn, accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en gebruikt vervolgens de [System.Management.Automation.Cmdlet.WriteObject% 28System.object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) methode als de uitvoer-mechanisme voor het verzenden van objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9ad21-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9ad21-105">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="9ad21-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->