---
title: Kenmerk typen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355627"
---
# <a name="attribute-types"></a>Typen kenmerken

Cmdlet-kenmerken kunnen worden gegroepeerd op functionaliteit.
In de volgende secties worden de beschik bare kenmerken beschreven en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.

## <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

### <a name="cmdlet"></a>De cmdlet

Identificeert een .NET Framework klasse als een cmdlet.
Dit is het vereiste basis kenmerk.
Zie voor meer informatie de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Parameter kenmerken

### <a name="parameter"></a>Parameter

Identificeert een open bare eigenschap in de cmdlet-klasse als een cmdlet-para meter.
Zie [para meter kenmerk declaratie](./parameter-attribute-declaration.md)voor meer informatie.

### <a name="alias"></a>Alias

Hiermee geeft u een of meer aliassen voor een para meter.
Zie [alias kenmerk declaratie](./alias-attribute-declaration.md)voor meer informatie.

## <a name="argument-validation-attributes"></a>Argument validatie kenmerken

### <a name="validatecount"></a>ValidateCount

Hiermee geeft u het minimum en maximum aantal argumenten op dat is toegestaan voor een cmdlet-para meter.
Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validatelength"></a>ValidateLength

Hiermee geeft u een minimum en maximum aantal tekens op voor een argument van een cmdlet-para meter.
Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validatepattern"></a>ValidatePattern

Hiermee geeft u een patroon van een reguliere expressie op dat het argument van de cmdlet-para meter moet overeenkomen.
Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validaterange"></a>ValidateRange

Hiermee geeft u de minimum-en maximum waarde op voor een argument van een cmdlet-para meter.
Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validateset"></a>Validatieset

Hiermee geeft u een set geldige waarden op voor het argument van de cmdlet-para meter.
Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Windows Power shell SDK](../windows-powershell-reference.md)
