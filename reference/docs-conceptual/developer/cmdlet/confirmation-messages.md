---
ms.date: 09/13/2016
ms.topic: reference
title: Bevestigingsberichten
description: Bevestigingsberichten
ms.openlocfilehash: 76302b2f8d8ca6dcdfe1b3c36f71aad23a53f7cf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355184"
---
# <a name="confirmation-messages"></a><span data-ttu-id="6388a-103">Bevestigingsberichten</span><span class="sxs-lookup"><span data-stu-id="6388a-103">Confirmation Messages</span></span>

<span data-ttu-id="6388a-104">Hier zijn verschillende bevestigings berichten die kunnen worden weer gegeven, afhankelijk van de varianten van de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) die worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="6388a-104">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6388a-105">Zie [bevestigingen aanvragen](./how-to-request-confirmations.md)voor een voorbeeld code waarin wordt getoond hoe u bevestigingen kunt aanvragen.</span><span class="sxs-lookup"><span data-stu-id="6388a-105">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="6388a-106">De resource opgeven</span><span class="sxs-lookup"><span data-stu-id="6388a-106">Specifying the Resource</span></span>

<span data-ttu-id="6388a-107">U kunt de resource opgeven die moet worden gewijzigd door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="6388a-107">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="6388a-108">In dit geval geeft u de resource op met behulp `target` van de para meter van de methode. de bewerking wordt toegevoegd door Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6388a-108">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="6388a-109">In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en de bewerking is de naam van de opdracht die de aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6388a-109">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6388a-110">Als de gebruiker **Ja** of **Ja selecteert voor** de bevestigings aanvraag (zoals weer gegeven in het volgende voor beeld), wordt een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6388a-110">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="6388a-111">De bewerking en resource opgeven</span><span class="sxs-lookup"><span data-stu-id="6388a-111">Specifying the Operation and Resource</span></span>

<span data-ttu-id="6388a-112">U kunt de resource opgeven die moet worden gewijzigd en de bewerking die de opdracht gaat uitvoeren door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="6388a-112">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="6388a-113">In dit geval geeft u de bron op met behulp van de `target` para meter en de bewerking met behulp van de `target` para meter.</span><span class="sxs-lookup"><span data-stu-id="6388a-113">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="6388a-114">In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en ' MyAction ' de bewerking die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6388a-114">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="6388a-115">Als de gebruiker **Ja** of **Ja selecteert voor** het vorige bericht, wordt een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6388a-115">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="6388a-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6388a-116">See Also</span></span>

[<span data-ttu-id="6388a-117">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="6388a-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
