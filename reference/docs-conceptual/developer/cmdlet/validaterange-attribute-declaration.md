---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateRange
description: Declaratie van het kenmerk ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660608"
---
# <a name="validaterange-attribute-declaration"></a>Declaratie van het kenmerk ValidateRange

Met het kenmerk ValidateRange worden de minimum-en maximum waarden (het bereik) opgegeven voor het argument van de cmdlet-para meter. Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameters

`MinRange` ([System. object](/dotnet/api/system.object)) vereist. Hiermee geeft u de toegestane minimum waarde.

`MaxRange` ([System. object](/dotnet/api/system.object)) vereist. Hiermee geeft u de toegestane maximum waarde.

## <a name="remarks"></a>Opmerkingen

- De Windows Power shell-runtime genereert een constructie fout wanneer de waarde van de `MinRange` para meter groter is dan de waarde van de `MaxRange` para meter.

- De Windows Power shell-runtime genereert een validatie fout in de volgende situaties:

  - Wanneer de waarde van het argument kleiner is dan de `MinRange` limiet of groter is dan de `MaxRange` limiet.

  - Wanneer het argument niet van hetzelfde type is als de `MinRange` `MaxRange` para meters en.

- Het kenmerk ValidateRange wordt gedefinieerd door de klasse [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
