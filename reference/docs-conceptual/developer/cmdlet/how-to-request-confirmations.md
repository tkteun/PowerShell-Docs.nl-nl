---
title: Bevestigingen aanvragen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359338"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="66a44-102">Bevestigingen aanvragen</span><span class="sxs-lookup"><span data-stu-id="66a44-102">How to Request Confirmations</span></span>

<span data-ttu-id="66a44-103">In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept om bevestigingen van de gebruiker aan te vragen voordat een actie wordt ondernomen.</span><span class="sxs-lookup"><span data-stu-id="66a44-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66a44-104">Voor meer informatie over hoe Windows Power shell deze aanvragen afhandelt, Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="66a44-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="66a44-105">Vragen om bevestiging</span><span class="sxs-lookup"><span data-stu-id="66a44-105">To request confirmation</span></span>

1. <span data-ttu-id="66a44-106">Zorg ervoor dat de para meter `SupportsShouldProcess` van het kenmerk cmdlet is ingesteld op `true`.</span><span class="sxs-lookup"><span data-stu-id="66a44-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="66a44-107">(Voor functions is dit een para meter van het kenmerk CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="66a44-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="66a44-108">Voeg een para meter `Force` toe aan uw cmdlet, zodat de gebruiker een bevestigings aanvraag kan onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="66a44-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="66a44-109">Voeg een instructie `if` toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om te bepalen of de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="66a44-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="66a44-110">Voeg een tweede `if`-instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en de waarde van de para meter `Force` om te bepalen of de bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="66a44-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="66a44-111">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="66a44-111">Example</span></span>

<span data-ttu-id="66a44-112">In het volgende code voorbeeld worden de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aangeroepen in de onderdrukking van de [ Methode System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="66a44-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="66a44-113">U kunt deze methoden echter ook aanroepen vanuit de andere invoer verwerkings methoden.</span><span class="sxs-lookup"><span data-stu-id="66a44-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="66a44-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="66a44-114">See Also</span></span>

[<span data-ttu-id="66a44-115">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="66a44-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
