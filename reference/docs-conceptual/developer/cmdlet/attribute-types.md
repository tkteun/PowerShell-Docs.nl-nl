---
ms.date: 09/13/2016
ms.topic: reference
title: Typen kenmerken
description: Typen kenmerken
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667110"
---
# <a name="attribute-types"></a>Typen kenmerken

Cmdlet-kenmerken kunnen worden gegroepeerd op functionaliteit.
In de volgende secties worden de beschik bare kenmerken beschreven en wordt beschreven wat de runtime doet wanneer het kenmerk wordt aangeroepen.

## <a name="cmdlet-attributes"></a>Cmdlet-kenmerken

### <a name="cmdlet"></a>Cmdlet

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

[Windows PowerShell SDK](../windows-powershell-reference.md)
