---
title: ValidateRange kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847535"
---
# <a name="validaterange-attribute-declaration"></a>Declaratie van het kenmerk ValidateRange

Het kenmerk ValidateRange Hiermee geeft u de minimale en maximale waarden (bereik) voor het argument van de cmdlet-parameter. Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parameters

`MinRange` ([System.Object](/dotnet/api/system.object)) vereist. Hiermee geeft u de minimaal toegestane waarde.

`MaxRange` ([System.Object](/dotnet/api/system.object)) vereist. Hiermee geeft u de maximaal toegestane waarde.

## <a name="remarks"></a>Opmerkingen

- De Windows PowerShell-runtime genereert een fout bouw wanneer de waarde van de `MinRange` parameter is groter dan de waarde van de `MaxRange` parameter.

- De Windows PowerShell-runtime genereert een fout in de volgende voorwaarden:

    - Wanneer de waarde van het argument is kleiner dan de `MinRange` beperken of groter is dan de `MaxRange` limiet.

    - Als het argument is niet van hetzelfde type als de `MinRange` en de `MaxRange` parameters.

- Het kenmerk ValidateRange wordt gedefinieerd door de [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
