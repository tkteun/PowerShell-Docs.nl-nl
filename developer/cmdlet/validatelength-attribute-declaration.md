---
title: ValidateLength kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067158"
---
# <a name="validatelength-attribute-declaration"></a>Declaratie van het kenmerk ValidateLength

Het kenmerk ValidateLength Hiermee geeft u het minimum en maximum aantal tekens in voor een argument van de cmdlet-parameter. Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.

## <a name="syntax"></a>Syntaxis

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parameters

`MinLength` ([System.Integer](/dotnet/api/System.Integer)) vereist. Hiermee geeft u het minimale aantal tekens dat is toegestaan.

`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) vereist. Hiermee geeft u het maximale aantal toegestane tekens.

## <a name="remarks"></a>Opmerkingen

- Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Wanneer dit kenmerk niet gebruikt wordt, wordt het bijbehorende parameterargument is van een willekeurige lengte.

- De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:

    - Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.

    - Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.

    - Als het argument is geen tekenreeks.

- Het kenmerk ValidateLength wordt gedefinieerd door de [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasse.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
