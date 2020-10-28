---
ms.date: 09/13/2016
ms.topic: reference
title: Parameter-invoer valideren
description: Parameter-invoer valideren
ms.openlocfilehash: a97b5c670e8c36463a85bbef1506f6311bdd5ec3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660394"
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

[Parameterinvoer valideren](./how-to-validate-parameter-input.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
