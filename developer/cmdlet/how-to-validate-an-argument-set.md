---
title: Het valideren van een Set voor Argument | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067707"
---
# <a name="how-to-validate-an-argument-set"></a><span data-ttu-id="116df-102">Een argumentenreeks valideren</span><span class="sxs-lookup"><span data-stu-id="116df-102">How to Validate an Argument Set</span></span>

<span data-ttu-id="116df-103">In dit voorbeeld laat zien hoe om op te geven van een regel voor het valideren dat de runtime van de Windows PowerShell gebruiken kunt om te controleren op het parameterargument voordat de cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="116df-103">This example shows how to specify a validation rule that the Windows PowerShell runtime can use to check the parameter argument before the cmdlet is run.</span></span> <span data-ttu-id="116df-104">Deze regel voor het valideren biedt een set met geldige waarden voor de parameterargument.</span><span class="sxs-lookup"><span data-stu-id="116df-104">This validation rule provides a set of the valid values for the parameter argument.</span></span>

> [!NOTE]
> <span data-ttu-id="116df-105">Zie voor meer informatie over de klasse die dit kenmerk definieert, [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span><span class="sxs-lookup"><span data-stu-id="116df-105">For more information about the class that defines this attribute, see [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute).</span></span>

## <a name="to-validate-an-argument-set"></a><span data-ttu-id="116df-106">Voor het valideren van een argument instellen</span><span class="sxs-lookup"><span data-stu-id="116df-106">To validate an argument set</span></span>

- <span data-ttu-id="116df-107">Voeg het kenmerk ValidateSet zoals wordt weergegeven in de volgende code.</span><span class="sxs-lookup"><span data-stu-id="116df-107">Add the ValidateSet attribute as shown in the following code.</span></span> <span data-ttu-id="116df-108">In dit voorbeeld geeft een reeks van drie mogelijke waarden voor de `UserName` parameter.</span><span class="sxs-lookup"><span data-stu-id="116df-108">This example specifies a set of three possible values for the `UserName` parameter.</span></span>

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

<span data-ttu-id="116df-109">Zie voor meer informatie over hoe u dit kenmerk declareren [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="116df-109">For more information about how to declare this attribute, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="116df-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="116df-110">See Also</span></span>

[<span data-ttu-id="116df-111">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="116df-111">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="116df-112">ValidateSet kenmerk declaratie</span><span class="sxs-lookup"><span data-stu-id="116df-112">ValidateSet Attribute Declaration</span></span>](./validateset-attribute-declaration.md)

[<span data-ttu-id="116df-113">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="116df-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
