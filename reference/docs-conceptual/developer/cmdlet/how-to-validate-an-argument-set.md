---
title: Een argument set valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356278"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="b2e02-102">Een argumentenreeks valideren</span><span class="sxs-lookup"><span data-stu-id="b2e02-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="b2e02-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b2e02-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="b2e02-104">Deze validatie regel bevat een set van de geldige waarden voor het parameter argument.</span><span class="sxs-lookup"><span data-stu-id="b2e02-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="b2e02-105">Zie [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b2e02-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="b2e02-106">Een argumentset valideren</span><span class="sxs-lookup"><span data-stu-id="b2e02-106">To validate an argument set</span></span>

- <span data-ttu-id="b2e02-107">Voeg het kenmerk validate toe, zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b2e02-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="b2e02-108">In dit voor beeld wordt een set van drie mogelijke waarden opgegeven voor de para meter `UserName`.</span><span class="sxs-lookup"><span data-stu-id="b2e02-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="b2e02-109">Zie [Validate-kenmerk declaratie](./validateset-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="b2e02-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2e02-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2e02-110">See Also</span></span>

[<span data-ttu-id="b2e02-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="b2e02-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b2e02-112">Verklaring van de kenmerkset validate</span><span class="sxs-lookup"><span data-stu-id="b2e02-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="b2e02-113">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b2e02-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
