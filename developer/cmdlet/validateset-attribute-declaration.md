---
title: ValidateSet kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067060"
---
# <a name="validateset-attribute-declaration"></a>Declaratie van het kenmerk ValidateSet

Het kenmerk ValidateSetAttribute geeft een reeks van mogelijke waarden voor een argument van de cmdlet-parameter. Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.

Wanneer dit kenmerk wordt opgegeven, wordt in de Windows PowerShell-runtime bepaalt of het opgegeven argument voor de cmdlet-parameter overeenkomt met een element in het opgegeven element instellen. De cmdlet wordt uitgevoerd alleen als het parameterargument overeenkomt met een element in de set. Als er geen overeenkomst wordt gevonden, wordt er door de Windows PowerShell-runtime een fout gegenereerd.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parameters

`ValidValues` ([System.String](/dotnet/api/System.String)) vereist. Hiermee geeft u de waarden van het element geldige parameter. Het volgende voorbeeld laat zien hoe een element of meerdere elementen op te geven.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. De standaardwaarde van `true` geeft aan dat de aanvraag wordt genegeerd. Een waarde van `false` kunt u de cmdlet hoofdlettergevoelig.

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk kan slechts één keer per parameter worden gebruikt.

- Als de waarde van parameter een matrix is, heeft elk element van de matrix moet overeenkomen met een element van het kenmerk is ingesteld.

- Het kenmerk ValidateSetAttribute wordt gedefinieerd door de [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
