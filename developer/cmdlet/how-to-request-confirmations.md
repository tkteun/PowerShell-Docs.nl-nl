---
title: Het aanvragen van bevestigingen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058816"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="b9e05-102">Bevestigingen aanvragen</span><span class="sxs-lookup"><span data-stu-id="b9e05-102">How to Request Confirmations</span></span>

<span data-ttu-id="b9e05-103">Dit voorbeeld laat zien hoe u aan te roepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden om aan te vragen van bevestigingen van de de gebruiker voordat een actie wordt ondernomen.</span><span class="sxs-lookup"><span data-stu-id="b9e05-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9e05-104">Zie voor meer informatie over hoe deze aanvragen worden verwerkt door Windows PowerShell, [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="b9e05-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="b9e05-105">Bevestiging</span><span class="sxs-lookup"><span data-stu-id="b9e05-105">To request confirmation</span></span>

1. <span data-ttu-id="b9e05-106">Zorg ervoor dat de `SupportsShouldProcess` parameter van de Cmdlet-kenmerk is ingesteld op `true`.</span><span class="sxs-lookup"><span data-stu-id="b9e05-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="b9e05-107">(Voor functions is dit een parameter van het kenmerk CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="b9e05-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="b9e05-108">Voeg een `Force` parameter aan uw cmdlet zodat de gebruiker een gebeurtenisbevestigingsaanvraag kunt negeren.</span><span class="sxs-lookup"><span data-stu-id="b9e05-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="b9e05-109">Voeg een `if` instructie die gebruikmaakt van de geretourneerde waarde van de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode om te bepalen of de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b9e05-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="b9e05-110">Voeg een tweede `if` instructie die gebruikmaakt van de geretourneerde waarde van de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode en de waarde van de `Force` parameter om te bepalen of de bewerking moet zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b9e05-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="b9e05-111">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="b9e05-111">Example</span></span>

<span data-ttu-id="b9e05-112">In het volgende codevoorbeeld wordt de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden zijn aangeroepen vanuit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode.</span><span class="sxs-lookup"><span data-stu-id="b9e05-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="b9e05-113">U kunt echter ook deze methoden aanroepen uit de andere invoer verwerkingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="b9e05-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b9e05-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b9e05-114">See Also</span></span>

[<span data-ttu-id="b9e05-115">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9e05-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
