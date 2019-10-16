---
title: Parameter invoer valideren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, validation rules
- validation, examples
- validation
ms.assetid: 3f15bf20-a068-4a7d-a170-bc43f755d1fe
caps.latest.revision: 14
ms.openlocfilehash: 171e3e974619e197a0bcc9dfc759297005e34568
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354878"
---
# <a name="validating-parameter-input"></a>Parameter-invoer valideren

Power shell kan de argumenten die zijn door gegeven aan cmdlet-para meters op verschillende manieren valideren.
In Power shell kunnen de lengte, het bereik en het patroon van de tekens van het argument worden gevalideerd.
Hiermee kan het aantal beschik bare argumenten (de telling) worden gevalideerd.
Deze validatie regels worden gedefinieerd door validatie kenmerken die zijn gedeclareerd met het parameter kenmerk voor open bare eigenschappen van de cmdlet-klasse.

Voor het valideren van een parameter argument gebruikt Power shell runtime de informatie die door de validatie kenmerken wordt verstrekt om de waarde van de para meter te bevestigen voordat de cmdlet wordt uitgevoerd.
Als de invoer van de para meter niet geldig is, ontvangt de gebruiker een fout bericht.
Elke validatie parameter definieert een validatie regel die door Power shell wordt afgedwongen.

Power shell dwingt de validatie regels af op basis van de volgende kenmerken.

### <a name="validatecount"></a>ValidateCount

Hiermee geeft u het minimum en maximum aantal argumenten op dat door een para meter kan worden geaccepteerd.
Zie [ValidateCount kenmerk declaratie](./validatecount-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validatelength"></a>ValidateLength

Hiermee geeft u het minimum en maximum aantal tekens in het parameter argument op.
Zie [ValidateLength kenmerk declaratie](./validatelength-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validatepattern"></a>ValidatePattern

Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.
Zie [ValidatePattern kenmerk declaratie](./validatepattern-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validaterange"></a>ValidateRange

Hiermee geeft u de minimum-en maximum waarden van het parameter argument op.
Zie [ValidateRange kenmerk declaratie](./validaterange-attribute-declaration.md)(Engelstalig) voor meer informatie.

### <a name="validateset"></a>Validatieset

Hiermee geeft u de geldige waarden voor het parameter argument op.
Zie [Validate kenmerk Declaration](./validateset-attribute-declaration.md)voor meer informatie.

## <a name="see-also"></a>Zie ook

[Parameter invoer valideren](./how-to-validate-parameter-input.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
