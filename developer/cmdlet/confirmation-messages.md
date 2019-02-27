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
# <a name="confirmation-messages"></a>Bevestigingsberichten

Hier volgen verschillende bevestigingsberichten die kunnen worden weergegeven, afhankelijk van de varianten van de [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden die worden aangeroepen.

> [!IMPORTANT]
> Zie voor een voorbeeld van code die laat zien hoe u aan te vragen van bevestigingen, [het verzoek bevestigingen](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>De Resource op te geven

U kunt opgeven dat de resource die moet worden gewijzigd door het aanroepen van de [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) methode. In dit geval het opgeven van de resource met behulp van de `target` parameter van de methode en de bewerking is toegevoegd door Windows PowerShell. In het volgende bericht: de tekst "MyResource" is de resource op een of meer bewerkingen en de bewerking is de naam van de opdracht die de aanroep.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Als de gebruiker selecteert **Ja** of **Ja op Alles** naar de bevestiging aanvragen (zoals weergegeven in het volgende voorbeeld), een aanroep naar de [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt gemaakt, waardoor een tweede bevestigingsbericht wordt weergegeven.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>De bewerking en de Resource op te geven

Kunt u de resource die moet worden gewijzigd en de bewerking die door de opdracht uitgevoerd is door het aanroepen van de [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) methode. In dit geval het opgeven van de resource met behulp van de `target` parameter en de bewerking met behulp van de `target` parameter. In het volgende bericht: de tekst "MyResource" is de resource op een of meer bewerkingen en "MyAction" is de bewerking die moet worden uitgevoerd.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Als de gebruiker selecteert **Ja** of **Ja op Alles** naar het vorige bericht, een aanroep naar de [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methode wordt gemaakt, waardoor een tweede bevestigingsbericht wordt weergegeven.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
