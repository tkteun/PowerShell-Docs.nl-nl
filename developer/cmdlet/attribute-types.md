---
title: Kenmerken van het type | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852274"
---
# <a name="attribute-types"></a>Typen kenmerken

Cmdlet kenmerken kunnen worden gegroepeerd op functionaliteit.
De volgende secties beschrijven de beschikbare kenmerken en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.

## <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

### <a name="cmdlet"></a>Cmdlet

Een .NET Framework-klasse identificeert als een cmdlet.
Dit is de vereiste base-kenmerk.
Zie voor meer informatie, [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameterkenmerken

### <a name="parameter"></a>Parameter

Een openbare eigenschap in de cmdlet-klasse wordt aangeduid als cmdlet-parameter.
Zie voor meer informatie, [kenmerk parameterdeclaratie](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Hiermee geeft u een of meer aliassen voor een parameter.
Zie voor meer informatie, [Alias kenmerkdeclaratie](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Argument validatie kenmerken

### <a name="validatecount"></a>ValidateCount

Hiermee geeft u het minimum en maximum aantal argumenten die zijn toegestaan voor een cmdlet-parameter.
Zie voor meer informatie, [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Hiermee geeft u een minimum en maximum aantal tekens in voor een argument van de cmdlet-parameter.
Zie voor meer informatie, [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Hiermee geeft u een reguliere-expressiepatroon dat moet overeenkomen met het argument van de cmdlet-parameter.
Zie voor meer informatie, [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Hiermee geeft u de minimale en maximale waarden voor een argument van de cmdlet-parameter.
Zie voor meer informatie, [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Hiermee geeft u een set met geldige waarden voor het argument van de cmdlet-parameter.
Zie voor meer informatie, [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
