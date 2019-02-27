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
ms.openlocfilehash: f7e5d4fb2f89bd6bc7036fdcff8f38e017d5d0e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848802"
---
# <a name="validating-parameter-input"></a>Parameter-invoer valideren

Windows PowerShell kunnen de argumenten doorgegeven aan de cmdlet-parameters in verschillende manieren worden gevalideerd. Windows PowerShell kunt valideren de lengte van het bereik en het patroon van de tekens van het argument. Dit kan het aantal argumenten beschikbaar (aantal) valideren. Deze validatieregels zijn gedefinieerd door validatie kenmerken die zijn gedeclareerd met de Parameter-kenmerk op openbare eigenschappen van de cmdlet-klasse.

Voor het valideren van een parameterargument gebruikt de Windows PowerShell-runtime de informatie die is geleverd door de kenmerken van de validatie te bevestigen van de waarde van de parameter voordat de cmdlet wordt uitgevoerd. Als de parameter-invoer niet geldig is, ontvangt de gebruiker een foutbericht weergegeven. Elke parameter validatie definieert een regel voor het valideren die door Windows PowerShell wordt afgedwongen.

Windows PowerShell de validatieregels op basis van de volgende kenmerken afgedwongen.

ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat een parameter kunt accepteren. Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateCount kenmerkdeclaratie](./validatecount-attribute-declaration.md).

ValidateLength Hiermee geeft u het minimum en maximum aantal tekens in de parameterargument. Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateLength kenmerkdeclaratie](./validatelength-attribute-declaration.md).

ValidatePattern Hiermee geeft u een reguliere expressie die het parameterargument valideert. Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidatePattern kenmerkdeclaratie](./validatepattern-attribute-declaration.md).

ValidateRange Hiermee geeft u de minimale en maximale waarden van de parameterargument. Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateRange kenmerkdeclaratie](./validaterange-attribute-declaration.md).

ValidateSet Hiermee geeft u de geldige waarden voor de parameterargument. Zie voor meer informatie over de syntaxis die is gebruikt om te declareren van dit kenmerk [ValidateSet kenmerkdeclaratie](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Zie ook

[Het valideren van de Parameter-invoer](./how-to-validate-parameter-input.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
