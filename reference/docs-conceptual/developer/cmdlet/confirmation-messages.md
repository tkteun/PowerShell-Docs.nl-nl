---
title: Bevestigings berichten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356432"
---
# <a name="confirmation-messages"></a><span data-ttu-id="243e2-102">Bevestigingsberichten</span><span class="sxs-lookup"><span data-stu-id="243e2-102">Confirmation Messages</span></span>

<span data-ttu-id="243e2-103">Hier zijn verschillende bevestigings berichten die kunnen worden weer gegeven, afhankelijk van de varianten van de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) die worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="243e2-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="243e2-104">Zie [bevestigingen aanvragen](./how-to-request-confirmations.md)voor een voorbeeld code waarin wordt getoond hoe u bevestigingen kunt aanvragen.</span><span class="sxs-lookup"><span data-stu-id="243e2-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="243e2-105">De resource opgeven</span><span class="sxs-lookup"><span data-stu-id="243e2-105">Specifying the Resource</span></span>

<span data-ttu-id="243e2-106">U kunt de resource opgeven die moet worden gewijzigd door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) .</span><span class="sxs-lookup"><span data-stu-id="243e2-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="243e2-107">In dit geval geeft u de bron op met behulp van de para meter `target` van de methode. de bewerking wordt toegevoegd door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="243e2-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="243e2-108">In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en de bewerking is de naam van de opdracht die de aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="243e2-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="243e2-109">Als de gebruiker **Ja** of **Ja selecteert voor** de bevestigings aanvraag (zoals weer gegeven in het volgende voor beeld), wordt een aanroep naar de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven weer.</span><span class="sxs-lookup"><span data-stu-id="243e2-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="243e2-110">De bewerking en resource opgeven</span><span class="sxs-lookup"><span data-stu-id="243e2-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="243e2-111">U kunt de resource opgeven die moet worden gewijzigd en de bewerking die de opdracht gaat uitvoeren door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) .</span><span class="sxs-lookup"><span data-stu-id="243e2-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="243e2-112">In dit geval geeft u de bron op met behulp van de para meter `target` en de bewerking met behulp van de para meter `target`.</span><span class="sxs-lookup"><span data-stu-id="243e2-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="243e2-113">In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en ' MyAction ' de bewerking die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="243e2-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="243e2-114">Als de gebruiker **Ja** of **Ja selecteert voor** het vorige bericht, wordt een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="243e2-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="243e2-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="243e2-115">See Also</span></span>

[<span data-ttu-id="243e2-116">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="243e2-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
