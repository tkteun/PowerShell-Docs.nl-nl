---
title: Het valideren van een argument aantal | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356292"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="e64b0-102">Het aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="e64b0-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="e64b0-103">In dit voor beeld ziet u hoe u een validatie regel opgeeft die door de Windows Power shell-runtime kan worden gebruikt om het aantal argumenten (de telling) te controleren dat door een para meter wordt geaccepteerd voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e64b0-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="e64b0-104">U stelt deze validatie regel in door het kenmerk ValidateCount te declareren.</span><span class="sxs-lookup"><span data-stu-id="e64b0-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="e64b0-105">Zie [System. Management. Automation. Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)voor meer informatie over de klasse waarmee dit kenmerk wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e64b0-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="e64b0-106">Een aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="e64b0-106">To validate an argument count</span></span>

- <span data-ttu-id="e64b0-107">Voeg het kenmerk validate toe, zoals wordt weer gegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="e64b0-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="e64b0-108">In dit voor beeld wordt aangegeven dat de para meter één argument of Maxi maal drie argumenten accepteert.</span><span class="sxs-lookup"><span data-stu-id="e64b0-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="e64b0-109">Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e64b0-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e64b0-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e64b0-110">See Also</span></span>

[<span data-ttu-id="e64b0-111">ValidateCount kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="e64b0-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="e64b0-112">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="e64b0-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
