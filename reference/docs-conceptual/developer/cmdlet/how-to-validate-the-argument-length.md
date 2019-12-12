---
title: De lengte van het argument valideren | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356264"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="80363-102">Een argumentlengte valideren</span><span class="sxs-lookup"><span data-stu-id="80363-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="80363-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door Windows Power shell runtime kan worden gebruikt om het aantal tekens (de lengte) van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="80363-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="80363-104">U stelt deze validatie regel in door het kenmerk ValidateLength te declareren.</span><span class="sxs-lookup"><span data-stu-id="80363-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="80363-105">Zie [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="80363-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="80363-106">De lengte van het argument valideren</span><span class="sxs-lookup"><span data-stu-id="80363-106">To validate the argument length</span></span>

- <span data-ttu-id="80363-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="80363-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="80363-108">In dit voor beeld wordt opgegeven dat de lengte van het argument een lengte van 0 tot 10 tekens moet hebben.</span><span class="sxs-lookup"><span data-stu-id="80363-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="80363-109">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="80363-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80363-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="80363-110">See Also</span></span>

[<span data-ttu-id="80363-111">ValidateLength kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="80363-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="80363-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="80363-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
