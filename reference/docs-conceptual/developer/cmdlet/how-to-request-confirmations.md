---
title: Bevestigingen aanvragen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784092"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="efcde-102">Bevestigingen aanvragen</span><span class="sxs-lookup"><span data-stu-id="efcde-102">How to Request Confirmations</span></span>

<span data-ttu-id="efcde-103">In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept om bevestigingen van de gebruiker aan te vragen voordat een actie wordt ondernomen.</span><span class="sxs-lookup"><span data-stu-id="efcde-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="efcde-104">Voor meer informatie over hoe Windows Power shell deze aanvragen afhandelt, Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="efcde-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="efcde-105">Vragen om bevestiging</span><span class="sxs-lookup"><span data-stu-id="efcde-105">To request confirmation</span></span>

1. <span data-ttu-id="efcde-106">Zorg ervoor dat de `SupportsShouldProcess` para meter van het cmdlet-kenmerk is ingesteld op `true` .</span><span class="sxs-lookup"><span data-stu-id="efcde-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="efcde-107">(Voor functions is dit een para meter van het kenmerk CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="efcde-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="efcde-108">Voeg een `Force` para meter toe aan de cmdlet, zodat de gebruiker een bevestigings aanvraag kan onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="efcde-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="efcde-109">Voeg een `if` instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om te bepalen of de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="efcde-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="efcde-110">Voeg een tweede `if` instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en de waarde van de `Force` para meter om te bepalen of de bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="efcde-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="efcde-111">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="efcde-111">Example</span></span>

<span data-ttu-id="efcde-112">In het volgende code voorbeeld worden de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aangeroepen in de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="efcde-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="efcde-113">U kunt deze methoden echter ook aanroepen vanuit de andere invoer verwerkings methoden.</span><span class="sxs-lookup"><span data-stu-id="efcde-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="efcde-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="efcde-114">See Also</span></span>

[<span data-ttu-id="efcde-115">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="efcde-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
