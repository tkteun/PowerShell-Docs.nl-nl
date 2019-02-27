---
title: ValidatePattern kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidatePattern
- ValidatePattern attribute, described
- ValidatePattern attribute
ms.assetid: 87b811be-6d93-4e7d-b9d0-c567a19bb0ef
caps.latest.revision: 13
ms.openlocfilehash: 5edcb65a6fbe1cb2fe2d0efe3f763fb84628b049
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848823"
---
# <a name="validatepattern-attribute-declaration"></a>Declaratie van het kenmerk ValidatePattern

Het kenmerk ValidatePattern Hiermee geeft u een reguliere-expressiepatroon dat het argument van een cmdlet-parameter worden gevalideerd. Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.

Wanneer ValidatePattern wordt opgeroepen binnen een cmdlet, wordt de Windows PowerShell-runtime wordt het argument van de cmdlet-parameter geconverteerd naar een tekenreeks en vergelijkt vervolgens die tekenreeks met het patroon dat is opgegeven door het kenmerk ValidatePattern. De cmdlet wordt uitgevoerd alleen als de geconverteerde tekenreeksweergave van het argument en het opgegeven patroon voldoen aan. Als ze niet overeenkomen, wordt er door de Windows PowerShell-runtime een fout gegenereerd.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parameters

`RegexString` ([System.String](/dotnet/api/System.String)) vereist. Hiermee geeft u een reguliere expressie die het parameterargument valideert.

Opties ([System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) met de naam van parameter optioneel. Hiermee geeft u een bitsgewijze combinatie van [System.Text.Regularexpressions.Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) vlaggen die reguliere expressie opgeven.

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk kan slechts één keer per parameter worden gebruikt.

- U kunt de `Option` parameter van het kenmerk om verder te definiëren het patroon. Bijvoorbeeld, kunt u het patroon hoofdlettergevoelig.

- Als dit kenmerk wordt toegepast op een verzameling, heeft elk element in de verzameling moet overeenkomen met het patroon.

- Het kenmerk ValidatePattern wordt gedefinieerd door de [System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
