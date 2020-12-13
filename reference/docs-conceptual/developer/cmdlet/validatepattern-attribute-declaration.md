---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidatePattern
description: Declaratie van het kenmerk ValidatePattern
ms.openlocfilehash: 364f63d2c52563eaefe64bcbb2bbae511bccb074
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646163"
---
# <a name="validatepattern-attribute-declaration"></a>Declaratie van het kenmerk ValidatePattern

Het kenmerk ValidatePattern geeft een patroon van een reguliere expressie op waarmee het argument van een cmdlet-para meter wordt gevalideerd. Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.

Wanneer ValidatePattern wordt aangeroepen binnen een cmdlet, converteert de Windows Power shell-runtime het argument van de cmdlet-para meter naar een teken reeks en vergelijkt die teken reeks met het patroon dat is opgegeven door het kenmerk ValidatePattern. De cmdlet wordt alleen uitgevoerd als de geconverteerde teken reeks weergave van het argument en het opgegeven patroon overeenkomen. Als ze niet overeenkomen, wordt er een fout gegenereerd door de Windows Power shell-runtime.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidatePattern(string regexString)]
[ValidatePattern(string regexString, Named Parameters)]
```

#### <a name="parameters"></a>Parameters

`RegexString` ([System. String](/dotnet/api/System.String)) vereist. Hiermee geeft u een reguliere expressie op waarmee het parameter argument wordt gevalideerd.

Opties ([System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions)) een optionele benoemde para meter. Hiermee geeft u een bitsgewijze combi natie van [System. Text. RegularExpressions. Regexoptions](/dotnet/api/System.Text.RegularExpressions.RegexOptions) -vlaggen op waarmee opties voor reguliere expressies worden opgegeven.

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.

- U kunt de `Option` para meter van het kenmerk gebruiken om het patroon verder te definiëren. U kunt bijvoorbeeld het patroon hoofdletter gevoelig maken.

- Als dit kenmerk wordt toegepast op een verzameling, moet elk element in de verzameling overeenkomen met het patroon.

- Het kenmerk ValidatePattern wordt gedefinieerd door de klasse [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
