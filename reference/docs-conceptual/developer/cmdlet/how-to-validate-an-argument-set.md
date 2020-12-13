---
ms.date: 09/13/2016
ms.topic: reference
title: Een argumentenreeks valideren
description: Een argumentenreeks valideren
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650367"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="b328e-103">Een argumentenreeks valideren</span><span class="sxs-lookup"><span data-stu-id="b328e-103">How to Validate an Argument Set</span></span>

<span data-ttu-id="b328e-104">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b328e-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="b328e-105">Deze validatie regel bevat een set van de geldige waarden voor het parameter argument.</span><span class="sxs-lookup"><span data-stu-id="b328e-105">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="b328e-106">Zie [System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b328e-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="b328e-107">Een argumentset valideren</span><span class="sxs-lookup"><span data-stu-id="b328e-107">To validate an argument set</span></span>

- <span data-ttu-id="b328e-108">Voeg het kenmerk validate toe, zoals in de volgende code wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b328e-108">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="b328e-109">In dit voor beeld wordt een set van drie mogelijke waarden voor de `UserName` para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b328e-109">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

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

<span data-ttu-id="b328e-110">Zie [Validate-kenmerk declaratie](./validateset-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="b328e-110">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b328e-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b328e-111">See Also</span></span>

[<span data-ttu-id="b328e-112">System. Management. Automation. Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="b328e-112">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="b328e-113">Declaratie van het kenmerk ValidateSet</span><span class="sxs-lookup"><span data-stu-id="b328e-113">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="b328e-114">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b328e-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
