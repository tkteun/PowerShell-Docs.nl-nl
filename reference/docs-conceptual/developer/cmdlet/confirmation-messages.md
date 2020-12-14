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
# <a name="confirmation-messages"></a>Bevestigingsberichten

Hier zijn verschillende bevestigings berichten die kunnen worden weer gegeven, afhankelijk van de varianten van de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) die worden aangeroepen.

> [!IMPORTANT]
> Zie [bevestigingen aanvragen](./how-to-request-confirmations.md)voor een voorbeeld code waarin wordt getoond hoe u bevestigingen kunt aanvragen.

## <a name="specifying-the-resource"></a>De resource opgeven

U kunt de resource opgeven die moet worden gewijzigd door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . In dit geval geeft u de resource op met behulp `target` van de para meter van de methode. de bewerking wordt toegevoegd door Windows Power shell. In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en de bewerking is de naam van de opdracht die de aanroep uitvoert.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Als de gebruiker **Ja** of **Ja selecteert voor** de bevestigings aanvraag (zoals weer gegeven in het volgende voor beeld), wordt een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>De bewerking en resource opgeven

U kunt de resource opgeven die moet worden gewijzigd en de bewerking die de opdracht gaat uitvoeren door het aanroepen van [System. Management. Automation. cmdlet. Shouldprocess% 2a? Methode Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . In dit geval geeft u de bron op met behulp van de `target` para meter en de bewerking met behulp van de `target` para meter. In het volgende bericht is de tekst ' MyResource ' de resource die wordt verwerkt en ' MyAction ' de bewerking die moet worden uitgevoerd.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Als de gebruiker **Ja** of **Ja selecteert voor** het vorige bericht, wordt een aanroep van de methode [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) uitgevoerd, waardoor een tweede bevestigings bericht wordt weer gegeven.

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
