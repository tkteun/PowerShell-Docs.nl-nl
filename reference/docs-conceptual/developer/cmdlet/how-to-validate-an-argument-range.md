---
ms.date: 09/13/2016
ms.topic: reference
title: Een argumentenbereik valideren
description: Een argumentenbereik valideren
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666923"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="1d641-103">Een argumentenbereik valideren</span><span class="sxs-lookup"><span data-stu-id="1d641-103">How to Validate an Argument Range</span></span>

<span data-ttu-id="1d641-104">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om de minimum-en maximum waarden van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1d641-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="1d641-105">U stelt deze validatie regel in door het kenmerk ValidateRange te declareren.</span><span class="sxs-lookup"><span data-stu-id="1d641-105">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="1d641-106">Zie [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="1d641-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="1d641-107">Een argument bereik valideren</span><span class="sxs-lookup"><span data-stu-id="1d641-107">To validate an argument range</span></span>

- <span data-ttu-id="1d641-108">Voeg het kenmerk ValidateRange toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="1d641-108">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="1d641-109">In dit voor beeld wordt een bereik van 0 tot 5 voor de `InputData` para meter opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1d641-109">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

<span data-ttu-id="1d641-110">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="1d641-110">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d641-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1d641-111">See Also</span></span>

[<span data-ttu-id="1d641-112">Declaratie van het kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="1d641-112">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="1d641-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="1d641-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
