---
title: Valideren van de invoer van de Parameter | Microsoft Docs
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
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429836"
---
# <a name="validating-parameter-input"></a>Parameter-invoer valideren

PowerShell kan de argumenten doorgegeven aan de cmdlet-parameters in verschillende manieren worden gevalideerd.
PowerShell kunt valideren de lengte van het bereik en het patroon van de tekens van het argument.
Dit kan het aantal argumenten beschikbaar (aantal) valideren.
Deze validatieregels zijn gedefinieerd door validatie kenmerken die zijn gedeclareerd met de Parameter-kenmerk op openbare eigenschappen van de cmdlet-klasse.

Voor het valideren van een parameterargument gebruikt de PowerShell-runtime de informatie die is geleverd door de kenmerken van de validatie te bevestigen van de waarde van de parameter voordat de cmdlet wordt uitgevoerd.
Als de parameter-invoer niet geldig is, ontvangt de gebruiker een foutbericht weergegeven.
Elke parameter validatie definieert een regel voor het valideren die wordt afgedwongen door PowerShell.

PowerShell de validatieregels op basis van de volgende kenmerken afgedwongen.

### <a name="validatecount"></a>ValidateCount

Hiermee geeft u het minimum en maximum aantal argumenten dat een parameter kunt accepteren.
Zie voor meer informatie, [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Hiermee geeft u het minimum en maximum aantal tekens in de parameterargument.
Zie voor meer informatie, [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Hiermee geeft u een reguliere expressie die het parameterargument valideert.
Zie voor meer informatie, [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Hiermee geeft u de minimale en maximale waarden van de parameterargument.
Zie voor meer informatie, [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Hiermee geeft u de geldige waarden voor de parameterargument.
Zie voor meer informatie, [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[Het valideren van de Parameter-invoer](./how-to-validate-parameter-input.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
