---
title: Alias kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782409"
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
