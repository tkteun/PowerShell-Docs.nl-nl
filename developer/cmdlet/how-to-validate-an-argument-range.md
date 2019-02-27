---
title: Het valideren van het bereik van een Argument | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849425"
---
# <a name="how-to-validate-an-argument-range"></a><span data-ttu-id="4351c-102">Een argumentenbereik valideren</span><span class="sxs-lookup"><span data-stu-id="4351c-102">How to Validate an Argument Range</span></span>

<span data-ttu-id="4351c-103">In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren of de minimale en maximale waarden van de parameterargument voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4351c-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the minimum and maximum values of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="4351c-104">U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateRange.</span><span class="sxs-lookup"><span data-stu-id="4351c-104">You set this validation rule by declaring the ValidateRange attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="4351c-105">Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span><span class="sxs-lookup"><span data-stu-id="4351c-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute).</span></span>

### <a name="to-validate-an-argument-range"></a><span data-ttu-id="4351c-106">Een argument adresbereik valideren</span><span class="sxs-lookup"><span data-stu-id="4351c-106">To validate an argument range</span></span>

- <span data-ttu-id="4351c-107">Voeg het kenmerk ValidateRange zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="4351c-107">Add the ValidateRange attribute as shown in the following code.</span></span> <span data-ttu-id="4351c-108">In dit voorbeeld geeft een bereik van 0 tot en met 5 voor de `InputData` parameter.</span><span class="sxs-lookup"><span data-stu-id="4351c-108">This example specifies a range of 0 to 5 for the `InputData` parameter.</span></span>

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

<span data-ttu-id="4351c-109">Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="4351c-109">For more information about how to declare this attribute, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4351c-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4351c-110">See Also</span></span>

[<span data-ttu-id="4351c-111">ValidateRange kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="4351c-111">ValidateRange Attribute Declaration</span></span>](./validaterange-attribute-declaration.md)

[<span data-ttu-id="4351c-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4351c-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
