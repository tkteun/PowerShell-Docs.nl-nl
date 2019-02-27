---
title: Alias kenmerkdeclaratie | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846142"
---
# <a name="alias-attribute-declaration"></a>Declaratie van het kenmerk Alias

Het kenmerk Alias kan de gebruiker om op te geven van verschillende namen voor een cmdlet-parameter. Aliassen kunnen worden gebruikt voor snelkoppelingen voor een parameternaam of ze verschillende namen die geschikt voor verschillende scenario's zijn kunnen opgeven.

## <a name="syntax"></a>Syntaxis

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parameters

`aliasName` (String[]) Vereist. Hiermee geeft u een set met de door komma's gescheiden aliasnamen van de cmdlet-parameter.

## <a name="remarks"></a>Opmerkingen

- Het kenmerk Alias wordt gebruikt met de Parameter-kenmerk wanneer u een cmdlet-parameter opgeven. Zie voor meer informatie over het declareren van deze kenmerken [hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md).

- De naam van elke alias moet uniek zijn binnen een cmdlet. Dubbele aliasnamen controleert niet op Windows PowerShell.

- Het kenmerk Alias wordt één keer gebruikt voor elke parameter in een cmdlet.

- De Alias-kenmerk wordt gedefinieerd door de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) klasse.

## <a name="see-also"></a>Zie ook

[Parameter Aliases](./parameter-aliases.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
