---
title: Het valideren van een patroon Argument | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067770"
---
# <a name="how-to-validate-an-argument-pattern"></a><span data-ttu-id="bb44d-102">Een argumentenpatroon valideren</span><span class="sxs-lookup"><span data-stu-id="bb44d-102">How to Validate an Argument Pattern</span></span>

<span data-ttu-id="bb44d-103">In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het teken-patroon van de parameterargument voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bb44d-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the character pattern of the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="bb44d-104">U kunt deze regel voor het valideren instellen door op te geven het kenmerk ValidatePattern.</span><span class="sxs-lookup"><span data-stu-id="bb44d-104">You set this validation rule by declaring the ValidatePattern attribute.</span></span>

> [!NOTE]
> <span data-ttu-id="bb44d-105">Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span><span class="sxs-lookup"><span data-stu-id="bb44d-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute).</span></span>

## <a name="to-validate-an-argument-pattern"></a><span data-ttu-id="bb44d-106">Voor het valideren van een argument-patroon</span><span class="sxs-lookup"><span data-stu-id="bb44d-106">To validate an argument pattern</span></span>

- <span data-ttu-id="bb44d-107">Voeg het kenmerk valideren zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="bb44d-107">Add the Validate attribute as shown in the following code.</span></span> <span data-ttu-id="bb44d-108">Dit voorbeeld wordt een patroon van vier cijfers, waarbij elk cijfer een waarde van 0 t/m 9 heeft.</span><span class="sxs-lookup"><span data-stu-id="bb44d-108">This example specifies a pattern of four digits, where each digit has a value of 0 through 9.</span></span>

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

<span data-ttu-id="bb44d-109">Zie voor meer informatie over hoe u dit kenmerk declareren [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bb44d-109">For more information about how to declare this attribute, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb44d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bb44d-110">See Also</span></span>

[<span data-ttu-id="bb44d-111">ValidatePattern kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="bb44d-111">ValidatePattern Attribute Declaration</span></span>](./validatepattern-attribute-declaration.md)

[<span data-ttu-id="bb44d-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bb44d-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
