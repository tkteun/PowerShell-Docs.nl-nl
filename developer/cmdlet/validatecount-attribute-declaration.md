---
title: ValidateCount kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794434"
---
# <a name="validatecount-attribute-declaration"></a>Declaratie van het kenmerk ValidateCount

Het kenmerk ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat is toegestaan voor een cmdlet-parameter.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) vereist. Hiermee geeft u het minimale aantal argumenten.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) vereist. Hiermee geeft u het maximum aantal argumenten.

## <a name="remarks"></a>Opmerkingen

- Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Als dit kenmerk niet gestart is, kan de bijbehorende cmdlet-parameter een willekeurig aantal argumenten hebben.

- De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:

    - De `MinLength` en `MaxLength` kenmerk parameters zijn niet van het type [System.Int32](/dotnet/api/System.Int32).

    - De waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.

- Het kenmerk ValidateCount wordt gedefinieerd door de [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Hoe u regels voor Invoervalidatie declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
