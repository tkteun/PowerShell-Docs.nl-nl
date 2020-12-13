---
ms.date: 09/13/2016
ms.topic: reference
title: Een argumentenpatroon valideren
description: Een argumentenpatroon valideren
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666906"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="35f24-103">Een argumentenpatroon valideren</span><span class="sxs-lookup"><span data-stu-id="35f24-103">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="35f24-104">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het teken patroon van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="35f24-104">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="35f24-105">U stelt deze validatie regel in door het kenmerk ValidatePattern te declareren.</span><span class="sxs-lookup"><span data-stu-id="35f24-105">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="35f24-106">Zie [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="35f24-106">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="35f24-107">Een argument patroon valideren</span><span class="sxs-lookup"><span data-stu-id="35f24-107">To validate an argument pattern</span></span>

- <span data-ttu-id="35f24-108">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="35f24-108">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="35f24-109">In dit voor beeld wordt een patroon van vier cijfers opgegeven, waarbij elk cijfer een waarde van 0 tot en met 9 heeft.</span><span class="sxs-lookup"><span data-stu-id="35f24-109">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

<span data-ttu-id="35f24-110">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="35f24-110">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="35f24-111">Zie ook</span><span class="sxs-lookup"><span data-stu-id="35f24-111">See Also</span></span>

[<span data-ttu-id="35f24-112">Declaratie van het kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="35f24-112">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="35f24-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="35f24-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
