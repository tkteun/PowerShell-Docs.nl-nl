---
title: Bevestigingsberichten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850601"
---
# <a name="confirmation-messages"></a><span data-ttu-id="7c1cc-102">Bevestigingsberichten</span><span class="sxs-lookup"><span data-stu-id="7c1cc-102">Confirmation Messages</span></span>

<span data-ttu-id="7c1cc-103">Hier volgen verschillende bevestigingsberichten die kunnen worden weergegeven, afhankelijk van de varianten van de [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [ System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden die worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c1cc-104">Zie voor een voorbeeld van code die laat zien hoe u aan te vragen van bevestigingen, [het verzoek bevestigingen](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="7c1cc-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="7c1cc-105">De Resource op te geven</span><span class="sxs-lookup"><span data-stu-id="7c1cc-105">Specifying the Resource</span></span>

<span data-ttu-id="7c1cc-106">U kunt opgeven dat de resource die moet worden gewijzigd door het aanroepen van de [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) methode.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="7c1cc-107">In dit geval het opgeven van de resource met behulp van de `target` parameter van de methode en de bewerking is toegevoegd door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="7c1cc-108">In het volgende bericht: de tekst "MyResource" is de resource op een of meer bewerkingen en de bewerking is de naam van de opdracht die de aanroep.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7c1cc-109">Als de gebruiker selecteert **Ja** of **Ja op Alles** naar de bevestiging aanvragen (zoals weergegeven in het volgende voorbeeld), een aanroep naar de [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt gemaakt, waardoor een tweede bevestigingsbericht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="7c1cc-110">De bewerking en de Resource op te geven</span><span class="sxs-lookup"><span data-stu-id="7c1cc-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="7c1cc-111">Kunt u de resource die moet worden gewijzigd en de bewerking die door de opdracht uitgevoerd is door het aanroepen van de [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) methode.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="7c1cc-112">In dit geval het opgeven van de resource met behulp van de `target` parameter en de bewerking met behulp van de `target` parameter.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="7c1cc-113">In het volgende bericht: de tekst "MyResource" is de resource op een of meer bewerkingen en "MyAction" is de bewerking die moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="7c1cc-114">Als de gebruiker selecteert **Ja** of **Ja op Alles** naar het vorige bericht, een aanroep naar de [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt gemaakt, waardoor een tweede bevestigingsbericht wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7c1cc-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="7c1cc-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7c1cc-115">See Also</span></span>

[<span data-ttu-id="7c1cc-116">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7c1cc-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
