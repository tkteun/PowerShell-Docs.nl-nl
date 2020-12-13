---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateLength
description: Declaratie van het kenmerk ValidateLength
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646188"
---
# <a name="validatelength-attribute-declaration"></a>Declaratie van het kenmerk ValidateLength

Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan. Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System. Int32](/dotnet/api/System.Int32)) vereist. Hiermee geeft u het minimum aantal tekens op dat is toegestaan.

`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) vereist. Hiermee geeft u het maximum aantal tekens op dat is toegestaan.

## <a name="remarks"></a>Opmerkingen

- Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.

- Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.

- De Windows Power shell-runtime genereert een fout in de volgende situaties:

  - Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` kenmerk parameter.

  - Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.

  - Wanneer het argument geen teken reeks is.

- Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
