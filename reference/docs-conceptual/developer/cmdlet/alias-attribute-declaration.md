---
title: Alias kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359484"
---
# <a name="alias-attribute-declaration"></a>Declaratie van het kenmerk Alias

Met het alias kenmerk kan de gebruiker verschillende namen opgeven voor een cmdlet-para meter. Aliassen kunnen worden gebruikt om snelkoppelingen voor de naam van een para meter op te geven, of ze kunnen verschillende namen opgeven die geschikt zijn voor verschillende scenario's.

## <a name="syntax"></a>Syntaxis

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parameters

`aliasName` (teken reeks []) is vereist. Hiermee geeft u een set met door komma's gescheiden alias namen op voor de cmdlet-para meter.

## <a name="remarks"></a>Opmerkingen

- Het kenmerk alias wordt gebruikt met het parameter kenmerk wanneer u een cmdlet-para meter opgeeft. Zie voor meer informatie over het declareren van deze kenmerken [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).

- Elke alias naam moet uniek zijn binnen een cmdlet. Windows Power shell controleert niet op dubbele alias namen.

- Het alias kenmerk wordt één keer gebruikt voor elke para meter in een cmdlet.

- Het alias kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Zie ook

[Parameter aliassen](./parameter-aliases.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
