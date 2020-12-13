---
ms.date: 09/13/2016
ms.topic: reference
title: Het aantal argumenten valideren
description: Het aantal argumenten valideren
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666940"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="a9c3d-103">Het aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="a9c3d-103">How to Validate an Argument Count</span></span>

<span data-ttu-id="a9c3d-104">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het aantal argumenten (de telling) te controleren dat door een para meter wordt geaccepteerd voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="a9c3d-105">U stelt deze validatie regel in door het kenmerk ValidateCount te declareren.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-105">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="a9c3d-106">Zie [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="a9c3d-107">Een aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="a9c3d-107">To validate an argument count</span></span>

- <span data-ttu-id="a9c3d-108">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="a9c3d-109">In dit voor beeld wordt aangegeven dat de para meter één argument of Maxi maal drie argumenten accepteert.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-109">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="a9c3d-110">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="a9c3d-110">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9c3d-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a9c3d-111">See Also</span></span>

[<span data-ttu-id="a9c3d-112">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="a9c3d-112">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="a9c3d-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="a9c3d-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
