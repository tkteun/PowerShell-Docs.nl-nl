---
title: Een argument patroon valideren | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782086"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="9bf67-102">Een argumentenpatroon valideren</span><span class="sxs-lookup"><span data-stu-id="9bf67-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="9bf67-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het teken patroon van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9bf67-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="9bf67-104">U stelt deze validatie regel in door het kenmerk ValidatePattern te declareren.</span><span class="sxs-lookup"><span data-stu-id="9bf67-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="9bf67-105">Zie [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="9bf67-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="9bf67-106">Een argument patroon valideren</span><span class="sxs-lookup"><span data-stu-id="9bf67-106">To validate an argument pattern</span></span>

- <span data-ttu-id="9bf67-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="9bf67-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="9bf67-108">In dit voor beeld wordt een patroon van vier cijfers opgegeven, waarbij elk cijfer een waarde van 0 tot en met 9 heeft.</span><span class="sxs-lookup"><span data-stu-id="9bf67-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="9bf67-109">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="9bf67-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bf67-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9bf67-110">See Also</span></span>

[<span data-ttu-id="9bf67-111">Declaratie van het kenmerk ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="9bf67-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="9bf67-112">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="9bf67-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
