---
title: Een argument patroon valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356313"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="99cd4-102">Een argumentenpatroon valideren</span><span class="sxs-lookup"><span data-stu-id="99cd4-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="99cd4-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het teken patroon van het parameter argument te controleren voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="99cd4-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="99cd4-104">U stelt deze validatie regel in door het kenmerk ValidatePattern te declareren.</span><span class="sxs-lookup"><span data-stu-id="99cd4-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="99cd4-105">Zie [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="99cd4-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="99cd4-106">Een argument patroon valideren</span><span class="sxs-lookup"><span data-stu-id="99cd4-106">To validate an argument pattern</span></span>

- <span data-ttu-id="99cd4-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="99cd4-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="99cd4-108">In dit voor beeld wordt een patroon van vier cijfers opgegeven, waarbij elk cijfer een waarde van 0 tot en met 9 heeft.</span><span class="sxs-lookup"><span data-stu-id="99cd4-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="99cd4-109">Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="99cd4-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="99cd4-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="99cd4-110">See Also</span></span>

[<span data-ttu-id="99cd4-111">ValidatePattern kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="99cd4-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="99cd4-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="99cd4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
