---
ms.date: 09/13/2016
ms.topic: reference
title: Bevestigingen aanvragen
description: Bevestigingen aanvragen
ms.openlocfilehash: 3e29803407bd9fbf13e6db0d0a02239c34e9c4fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666991"
---
# <a name="how-to-request-confirmations"></a>Bevestigingen aanvragen

In dit voor beeld ziet u hoe u de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aanroept om bevestigingen van de gebruiker aan te vragen voordat een actie wordt ondernomen.

> [!IMPORTANT]
> Voor meer informatie over hoe Windows Power shell deze aanvragen afhandelt, Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Vragen om bevestiging

1. Zorg ervoor dat de `SupportsShouldProcess` para meter van het cmdlet-kenmerk is ingesteld op `true` . (Voor functions is dit een para meter van het kenmerk CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Voeg een `Force` para meter toe aan de cmdlet, zodat de gebruiker een bevestigings aanvraag kan onderdrukken.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Voeg een `if` instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om te bepalen of de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wordt aangeroepen.

4. Voeg een tweede `if` instructie toe die gebruikmaakt van de retour waarde van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) en de waarde van de `Force` para meter om te bepalen of de bewerking moet worden uitgevoerd.

## <a name="example"></a>Voorbeeld

In het volgende code voorbeeld worden de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) aangeroepen in de onderdrukking van de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . U kunt deze methoden echter ook aanroepen vanuit de andere invoer verwerkings methoden.

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

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
