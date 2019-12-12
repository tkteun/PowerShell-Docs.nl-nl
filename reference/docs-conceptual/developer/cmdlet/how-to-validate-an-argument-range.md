---
title: Een argument bereik valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356285"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="8e31e-102">Een argumentenbereik valideren</span><span class="sxs-lookup"><span data-stu-id="8e31e-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="8e31e-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om de minimum-en maximum waarden van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8e31e-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="8e31e-104">U stelt deze validatie regel in door het kenmerk ValidateRange te declareren.</span><span class="sxs-lookup"><span data-stu-id="8e31e-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="8e31e-105">Zie [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="8e31e-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="8e31e-106">Een argument bereik valideren</span><span class="sxs-lookup"><span data-stu-id="8e31e-106">To validate an argument range</span></span>

- <span data-ttu-id="8e31e-107">Voeg het kenmerk ValidateRange toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="8e31e-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="8e31e-108">In dit voor beeld wordt een bereik van 0 tot 5 opgegeven voor de para meter `InputData`.</span><span class="sxs-lookup"><span data-stu-id="8e31e-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="8e31e-109">Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="8e31e-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8e31e-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8e31e-110">See Also</span></span>

[<span data-ttu-id="8e31e-111">ValidateRange kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="8e31e-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="8e31e-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="8e31e-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
