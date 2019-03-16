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
# <a name="how-to-request-confirmations"></a>Bevestigingen aanvragen

Dit voorbeeld laat zien hoe u aan te roepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden om aan te vragen van bevestigingen van de de gebruiker voordat een actie wordt ondernomen.

> [!IMPORTANT]
> Zie voor meer informatie over hoe deze aanvragen worden verwerkt door Windows PowerShell, [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Bevestiging

1. Zorg ervoor dat de `SupportsShouldProcess` parameter van de Cmdlet-kenmerk is ingesteld op `true`. (Voor functions is dit een parameter van het kenmerk CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Voeg een `Force` parameter aan uw cmdlet zodat de gebruiker een gebeurtenisbevestigingsaanvraag kunt negeren.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Voeg een `if` instructie die gebruikmaakt van de geretourneerde waarde van de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode om te bepalen of de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt aangeroepen.

4. Voeg een tweede `if` instructie die gebruikmaakt van de geretourneerde waarde van de [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode en de waarde van de `Force` parameter om te bepalen of de bewerking moet zijn uitgevoerd.

## <a name="example"></a>Voorbeeld

In het volgende codevoorbeeld wordt de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden zijn aangeroepen vanuit de onderdrukking van de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode. U kunt echter ook deze methoden aanroepen uit de andere invoer verwerkingsmethoden.

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
