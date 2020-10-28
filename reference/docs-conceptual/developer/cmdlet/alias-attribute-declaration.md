---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk Alias
description: Declaratie van het kenmerk Alias
ms.openlocfilehash: f2fe49578da2c795643b1f80fa44deefe1dbff09
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668300"
---
# <a name="alias-attribute-declaration"></a>Declaratie van het kenmerk Alias

Met het alias kenmerk kan de gebruiker verschillende namen opgeven voor een cmdlet-para meter. Aliassen kunnen worden gebruikt om snelkoppelingen voor de naam van een para meter op te geven, of ze kunnen verschillende namen opgeven die geschikt zijn voor verschillende scenario's.

## <a name="syntax"></a>Syntaxis

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parameters

`aliasName` (Teken reeks []) Vereist. Hiermee geeft u een set met door komma's gescheiden alias namen op voor de cmdlet-para meter.

## <a name="remarks"></a>Opmerkingen

- Het kenmerk alias wordt gebruikt met het parameter kenmerk wanneer u een cmdlet-para meter opgeeft. Zie voor meer informatie over het declareren van deze kenmerken [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).

- Elke alias naam moet uniek zijn binnen een cmdlet. Windows Power shell controleert niet op dubbele alias namen.

- Het alias kenmerk wordt één keer gebruikt voor elke para meter in een cmdlet.

- Het alias kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Zie ook

[Parameteraliassen](./parameter-aliases.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
