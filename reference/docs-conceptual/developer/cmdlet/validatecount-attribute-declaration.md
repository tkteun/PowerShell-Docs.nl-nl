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
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692367"
---
# <a name="validatecount-attribute-declaration"></a>Declaratie van het kenmerk ValidateCount

Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength`([System. Int32][]) vereist. Hiermee geeft u het minimum aantal argumenten op.

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
