---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateSet
description: Declaratie van het kenmerk ValidateSet
ms.openlocfilehash: 7894d00561366ada492911e8147acbd8d3454a55
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660470"
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

`ValidValues` ([System. String](/dotnet/api/System.String)) vereist. Hiermee geeft u de geldige parameter element waarden op. Het volgende voor beeld laat zien hoe u één element of meerdere elementen kunt opgeven.

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

`IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. De standaard waarde van `true` geeft aan dat de aanvraag wordt genegeerd. De waarde van `false` de cmdlet is hoofdletter gevoelig.

## <a name="remarks"></a>Opmerkingen

- Dit kenmerk kan slechts eenmaal per para meter worden gebruikt.

- Als de parameter waarde een matrix is, moet elk element van de matrix overeenkomen met een element van de kenmerkset.

- Het kenmerk ValidateSetAttribute wordt gedefinieerd door de klasse [System. Management. Automation. ValidateSetAttribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) .

## <a name="see-also"></a>Zie ook

[System. Management. Automation. Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
