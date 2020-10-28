---
ms.date: 09/13/2016
ms.topic: reference
title: Kenmerken in de cmdlet-code
description: Kenmerken in de cmdlet-code
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653642"
---
# <a name="attributes-in-cmdlet-code"></a>Kenmerken in de cmdlet-code

Als u de algemene functionaliteit van Windows Power shell wilt gebruiken, worden de klassen en open bare eigenschappen die in de cmdlet-code zijn gedefinieerd, voorzien van kenmerken. De volgende klassen definitie maakt bijvoorbeeld gebruik van het cmdlet-kenmerk om de Microsoft .NET Framework-klasse te identificeren waarin de **Get-proc-** cmdlet wordt geïmplementeerd. (Deze cmdlet wordt gebruikt als voor beeld in dit document en is vergelijkbaar met de `Get-Process` cmdlet van Windows Power shell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Deze kenmerken worden beschouwd als meta gegevens omdat hun implementatie gescheiden is van de implementatie van de cmdlet-code. Wanneer de Windows Power shell-runtime de cmdlet uitvoert, herkent deze de kenmerken en voert vervolgens de juiste actie uit voor elk kenmerk.

Hoewel het mogelijk is om uw eigen versie van de functionaliteit van deze kenmerken te implementeren, maakt een goed ontwerp van de cmdlet gebruik van deze algemene functies.

Zie [kenmerk typen](./attribute-types.md)voor meer informatie over de verschillende kenmerken die kunnen worden gedeclareerd in de-cmdlets.

## <a name="see-also"></a>Zie ook

[Typen kenmerken](./attribute-types.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
