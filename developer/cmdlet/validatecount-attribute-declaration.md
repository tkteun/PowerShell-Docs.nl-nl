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
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983895"
---
# <a name="validatecount-attribute-declaration"></a>Declaratie van het kenmerk ValidateCount

Het kenmerk ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat is toegestaan voor een cmdlet-parameter.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System.Int32][]) vereist. Hiermee geeft u het minimale aantal argumenten.

`MaxLength`([System.Int32][]) vereist. Hiermee geeft u het maximum aantal argumenten.

## <a name="remarks"></a>Opmerkingen

- Zie voor meer informatie over hoe u dit kenmerk declareren [het valideren van een aantal argumenten][].

- Als dit kenmerk niet gestart is, kan de bijbehorende cmdlet-parameter een willekeurig aantal argumenten hebben.

- De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:

    - De `MinLength` en `MaxLength` kenmerk parameters zijn niet van het type [System.Int32][].

    - De waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.

- Het kenmerk ValidateCount wordt gedefinieerd door de [System.Management.Automation.ValidateCountAttribute][] klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.ValidateCountAttribute][]

[Het valideren van een aantal argumenten][]

[Schrijven van een Windows PowerShell-Cmdlet][]

[Het valideren van een aantal argumenten]: how-to-validate-an-argument-count.md
[Schrijven van een Windows PowerShell-Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
