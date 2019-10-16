---
title: ValidateRange kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359133"
---
# <a name="validaterange-attribute-declaration"></a>Declaratie van het kenmerk ValidateRange

Met het kenmerk ValidateRange worden de minimum-en maximum waarden (het bereik) opgegeven voor het argument van de cmdlet-para meter. Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameters

`MinRange` ([System. object](/dotnet/api/system.object)) is vereist. Hiermee geeft u de toegestane minimum waarde.

`MaxRange` ([System. object](/dotnet/api/system.object)) is vereist. Hiermee geeft u de toegestane maximum waarde.

## <a name="remarks"></a>Opmerkingen

- De Windows Power shell-runtime genereert een constructie fout wanneer de waarde van de para meter `MinRange` groter is dan de waarde van de para meter `MaxRange`.

- De Windows Power shell-runtime genereert een validatie fout in de volgende situaties:

    - Wanneer de waarde van het argument kleiner is dan de limiet van @no__t 0 of groter is dan de limiet van `MaxRange`.

    - Wanneer het argument niet van hetzelfde type is als de `MinRange` en de para meters `MaxRange`.

- Het kenmerk ValidateRange wordt gedefinieerd door de klasse [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
