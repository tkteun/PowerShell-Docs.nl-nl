---
title: Verklaring van de kenmerkset validate | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355417"
---
# <a name="validateset-attribute-declaration"></a>Declaratie van het kenmerk ValidateSet

Het kenmerk ValidateSetAttribute bevat een reeks mogelijke waarden voor een argument van een cmdlet-para meter. Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.

Als dit kenmerk is opgegeven, bepaalt de Windows Power shell-runtime of het opgegeven argument voor de cmdlet-para meter overeenkomt met een element in de opgegeven verzameling van elementen. De cmdlet wordt alleen uitgevoerd als het parameter argument overeenkomt met een element in de set. Als er geen overeenkomst wordt gevonden, wordt er een fout gegenereerd door de Windows Power shell-runtime.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a>Parameters

`ValidValues` ([System. String](/dotnet/api/System.String)) is vereist. Hiermee geeft u de geldige parameter element waarden op. Het volgende voor beeld laat zien hoe u één element of meerdere elementen kunt opgeven.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. De standaard waarde van `true` geeft aan dat het geval wordt genegeerd. Met de waarde `false` wordt de cmdlet hoofdletter gevoelig gemaakt.

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.

- Als de parameter waarde een matrix is, moet elk element van de matrix overeenkomen met een element van de kenmerkset.

- Het kenmerk ValidateSetAttribute wordt gedefinieerd door de klasse [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
