---
title: Het valideren van de lengte van het Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067706"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="43d03-102">Een argumentlengte valideren</span><span class="sxs-lookup"><span data-stu-id="43d03-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="43d03-103">In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het aantal tekens (de lengte) van de parameterargument voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="43d03-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="43d03-104">U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateLength.</span><span class="sxs-lookup"><span data-stu-id="43d03-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="43d03-105">Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span><span class="sxs-lookup"><span data-stu-id="43d03-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="43d03-106">De lengte van het argument valideren</span><span class="sxs-lookup"><span data-stu-id="43d03-106">To validate the argument length</span></span>

- <span data-ttu-id="43d03-107">Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="43d03-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="43d03-108">In dit voorbeeld geeft aan dat de lengte van het argument een lengte van 0 tot en met 10 tekens moet zijn.</span><span class="sxs-lookup"><span data-stu-id="43d03-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="43d03-109">Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="43d03-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43d03-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43d03-110">See Also</span></span>

[<span data-ttu-id="43d03-111">ValidateLength kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="43d03-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="43d03-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="43d03-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
