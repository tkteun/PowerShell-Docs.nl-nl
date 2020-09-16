---
title: Output type kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786540"
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
