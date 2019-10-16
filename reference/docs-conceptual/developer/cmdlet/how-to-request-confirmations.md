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
# <a name="how-to-request-confirmations"></a>Bevestigingen aanvragen

In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept om bevestigingen van de gebruiker aan te vragen voordat een actie wordt ondernomen.

> [!IMPORTANT]
> Voor meer informatie over hoe Windows Power shell deze aanvragen afhandelt, Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Vragen om bevestiging

1. Zorg ervoor dat de para meter `SupportsShouldProcess` van het kenmerk cmdlet is ingesteld op `true`. (Voor functions is dit een para meter van het kenmerk CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Voeg een para meter `Force` toe aan uw cmdlet, zodat de gebruiker een bevestigings aanvraag kan onderdrukken.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Voeg een instructie `if` toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om te bepalen of de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wordt aangeroepen.

4. Voeg een tweede `if`-instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en de waarde van de para meter `Force` om te bepalen of de bewerking moet worden uitgevoerd.

## <a name="example"></a>Voorbeeld

In het volgende code voorbeeld worden de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aangeroepen in de onderdrukking van de [ Methode System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . U kunt deze methoden echter ook aanroepen vanuit de andere invoer verwerkings methoden.

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

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
