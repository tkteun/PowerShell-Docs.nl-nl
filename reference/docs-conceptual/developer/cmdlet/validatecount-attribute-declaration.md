---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateCount
description: Declaratie van het kenmerk ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646269"
---
# <a name="validatecount-attribute-declaration"></a>Declaratie van het kenmerk ValidateCount

Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System. Int32][]) vereist. Hiermee geeft u het minimum aantal argumenten op.

`MaxLength`([System. Int32][]) vereist. Hiermee geeft u het maximum aantal argumenten op.

## <a name="remarks"></a>Opmerkingen

- Zie [How to validate a argument Count][](Engelstalig) voor meer informatie over het declareren van dit kenmerk.

- Als dit kenmerk niet wordt aangeroepen, kan de bijbehorende cmdlet-para meter een wille keurig aantal argumenten hebben.

- De Windows Power shell-runtime genereert een fout in de volgende situaties:

  - De `MinLength` `MaxLength` para meters en zijn niet van het type [System. Int32][].

  - De waarde van de `MaxLength` kenmerk parameter is kleiner dan de waarde van de `MinLength` kenmerk parameter.

- Het kenmerk ValidateCount wordt gedefinieerd door de klasse [System. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. ValidateCountAttribute][]

[Het aantal argumenten valideren][]

[Een Windows PowerShell-cmdlet schrijven][]

[Het aantal argumenten valideren]: how-to-validate-an-argument-count.md
[Een Windows PowerShell-cmdlet schrijven]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
