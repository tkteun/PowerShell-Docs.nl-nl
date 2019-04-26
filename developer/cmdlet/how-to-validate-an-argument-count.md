---
title: Het valideren van een aantal argumenten | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067804"
---
# <a name="how-to-validate-an-argument-count"></a><span data-ttu-id="2a863-102">Het aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="2a863-102">How to Validate an Argument Count</span></span>

<span data-ttu-id="2a863-103">Dit voorbeeld laat zien hoe u kunt een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren of het aantal argumenten (aantal) die een parameter accepteert opgeven voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2a863-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the number of arguments (the count) that a parameter accepts before the cmdlet is run.</span></span> <span data-ttu-id="2a863-104">U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidateCount.</span><span class="sxs-lookup"><span data-stu-id="2a863-104">You set this validation rule by declaring the ValidateCount attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="2a863-105">Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span><span class="sxs-lookup"><span data-stu-id="2a863-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute).</span></span>

## <a name="to-validate-an-argument-count"></a><span data-ttu-id="2a863-106">Een aantal argumenten valideren</span><span class="sxs-lookup"><span data-stu-id="2a863-106">To validate an argument count</span></span>

- <span data-ttu-id="2a863-107">Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="2a863-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="2a863-108">In dit voorbeeld geeft aan dat de parameter één argument of maximaal drie argumenten accepteert.</span><span class="sxs-lookup"><span data-stu-id="2a863-108">This example specifies that the parameter will accept one argument or as many as three arguments.</span></span>

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

<span data-ttu-id="2a863-109">Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="2a863-109">For more information about how to declare this attribute, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a863-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2a863-110">See Also</span></span>

[<span data-ttu-id="2a863-111">ValidateCount kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="2a863-111">ValidateCount Attribute Declaration</span></span>](./validatecount-attribute-declaration.md)

[<span data-ttu-id="2a863-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2a863-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
