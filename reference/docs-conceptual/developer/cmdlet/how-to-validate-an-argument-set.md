---
title: Een argument set valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782001"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="d8f8c-102">Een argumentenreeks valideren</span><span class="sxs-lookup"><span data-stu-id="d8f8c-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="d8f8c-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="d8f8c-104">Deze validatie regel bevat een set van de geldige waarden voor het parameter argument.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="d8f8c-105">Zie [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="d8f8c-106">Een argumentset valideren</span><span class="sxs-lookup"><span data-stu-id="d8f8c-106">To validate an argument set</span></span>

- <span data-ttu-id="d8f8c-107">Voeg het kenmerk validate toe, zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="d8f8c-108">In dit voor beeld wordt een set van drie mogelijke waarden voor de `UserName` para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="d8f8c-109">Zie [Validate-kenmerk declaratie](./validateset-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="d8f8c-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8f8c-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d8f8c-110">See Also</span></span>

[<span data-ttu-id="d8f8c-111">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="d8f8c-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="d8f8c-112">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="d8f8c-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="d8f8c-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="d8f8c-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
