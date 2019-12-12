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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359143"
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

- U kunt de para meter `Option` van het kenmerk gebruiken om het patroon verder te definiëren. U kunt bijvoorbeeld het patroon hoofdletter gevoelig maken.

- Als dit kenmerk wordt toegepast op een verzameling, moet elk element in de verzameling overeenkomen met het patroon.

- Het kenmerk ValidatePattern wordt gedefinieerd door de klasse [System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
