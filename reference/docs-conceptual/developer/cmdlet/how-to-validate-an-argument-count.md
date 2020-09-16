---
title: Het valideren van een argument aantal | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateCount attribute, example
ms.openlocfilehash: e7c0eb364a6975cec089b984c2100d476631a12d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782120"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="9f53c-102">Het aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="9f53c-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="9f53c-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het aantal argumenten (de telling) te controleren dat door een para meter wordt geaccepteerd voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f53c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="9f53c-104">U stelt deze validatie regel in door het kenmerk ValidateCount te declareren.</span><span class="sxs-lookup"><span data-stu-id="9f53c-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="9f53c-105">Zie [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9f53c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="9f53c-106">Een aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="9f53c-106">To validate an argument count</span></span>

- <span data-ttu-id="9f53c-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="9f53c-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="9f53c-108">In dit voor beeld wordt aangegeven dat de para meter één argument of Maxi maal drie argumenten accepteert.</span><span class="sxs-lookup"><span data-stu-id="9f53c-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

<span data-ttu-id="9f53c-109">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="9f53c-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f53c-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9f53c-110">See Also</span></span>

[<span data-ttu-id="9f53c-111">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="9f53c-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="9f53c-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="9f53c-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
