---
title: De lengte van het argument valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, example
ms.openlocfilehash: aa0545def6d9628f6b41090a425f0c5af25f6ad7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784075"
---
# <a name="how-to-validate-the-argument-length"></a><span data-ttu-id="17f2d-102">Een argumentlengte valideren</span><span class="sxs-lookup"><span data-stu-id="17f2d-102">How to Validate the Argument Length</span></span>

<span data-ttu-id="17f2d-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door Windows Power shell runtime kan worden gebruikt om het aantal tekens (de lengte) van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="17f2d-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of characters (the length) of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="17f2d-104">U stelt deze validatie regel in door het kenmerk ValidateLength te declareren.</span><span class="sxs-lookup"><span data-stu-id="17f2d-104">You set this validation rule by declaring the ValidateLength attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="17f2d-105">Zie [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="17f2d-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute).</span></span>

## <a name="to-validate-the-argument-length"></a><span data-ttu-id="17f2d-106">De lengte van het argument valideren</span><span class="sxs-lookup"><span data-stu-id="17f2d-106">To validate the argument length</span></span>

- <span data-ttu-id="17f2d-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="17f2d-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="17f2d-108">In dit voor beeld wordt opgegeven dat de lengte van het argument een lengte van 0 tot 10 tekens moet hebben.</span><span class="sxs-lookup"><span data-stu-id="17f2d-108">This example specifies that the length of the argument should have a length of 0 to 10 characters.</span></span>

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

<span data-ttu-id="17f2d-109">Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="17f2d-109">For more information about how to declare this attribute, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17f2d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="17f2d-110">See Also</span></span>

[<span data-ttu-id="17f2d-111">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="17f2d-111">ValidateLength Attribute Declaration</span></span>](./validatelength-attribute-declaration.md)

[<span data-ttu-id="17f2d-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="17f2d-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
