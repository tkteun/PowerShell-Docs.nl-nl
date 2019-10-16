---
title: Output type kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356159"
---
# <a name="outputtype-attribute-declaration"></a>Declaratie van het kenmerk OutputType

Het kenmerk `OutputType` identificeert de .NET Framework typen die door een cmdlet, functie of script worden geretourneerd.

## <a name="syntax"></a>Syntaxis

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

Type (`string[]` of `Type[]`) vereist. Hiermee geeft u de typen op die worden geretourneerd door de functie cmdlet of het script.

ParameterSetName (string []) optioneel. Hiermee geeft u de parameter sets op die de typen retour neren die zijn opgegeven in de para meter `type`.

providerCmdlet optioneel. Hiermee geeft u de provider-cmdlet op waarmee de typen worden geretourneerd die zijn opgegeven in de para meter `type`.

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
