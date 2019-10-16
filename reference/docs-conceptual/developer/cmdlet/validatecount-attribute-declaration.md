---
title: ValidateCount kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359166"
---
# <a name="validatecount-attribute-declaration"></a>Declaratie van het kenmerk ValidateCount

Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System. Int32][]) is vereist. Hiermee geeft u het minimum aantal argumenten op.

`MaxLength` ([System. Int32][]) is vereist. Hiermee geeft u het maximum aantal argumenten op.

## <a name="remarks"></a>Opmerkingen

- Zie [Een aantal argumenten valideren][](Engelstalig) voor meer informatie over het declareren van dit kenmerk.

- Als dit kenmerk niet wordt aangeroepen, kan de bijbehorende cmdlet-para meter een wille keurig aantal argumenten hebben.

- De Windows Power shell-runtime genereert een fout in de volgende situaties:

    - De kenmerk parameters `MinLength` en `MaxLength` zijn niet van het type [System. Int32][].

    - De waarde van de para meter `MaxLength`-kenmerk is kleiner dan de waarde van de para meter `MinLength`-kenmerk.

- Het kenmerk ValidateCount wordt gedefinieerd door de klasse [System. Management. Automation. ValidateCountAttribute][] .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. ValidateCountAttribute][]

[Een aantal argumenten valideren][]

[Een Windows Power shell-cmdlet schrijven][]

[Een aantal argumenten valideren]: how-to-validate-an-argument-count.md
[Een Windows Power shell-cmdlet schrijven]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
