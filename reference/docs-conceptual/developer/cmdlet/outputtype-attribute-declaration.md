---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk OutputType
description: Declaratie van het kenmerk OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646455"
---
# <a name="outputtype-attribute-declaration"></a>Declaratie van het kenmerk OutputType

Het `OutputType` kenmerk identificeert de .NET Framework typen die worden geretourneerd door een cmdlet, functie of script.

## <a name="syntax"></a>Syntaxis

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

Type ( `string[]` of `Type[]` ) vereist. Hiermee geeft u de typen op die worden geretourneerd door de functie cmdlet of het script.

ParameterSetName (string []) optioneel. Hiermee geeft u de parameter sets op die de typen retour neren die zijn opgegeven in de `type` para meter.

providerCmdlet optioneel. Hiermee geeft u de provider-cmdlet op waarmee de typen worden geretourneerd die zijn opgegeven in de `type` para meter.

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
