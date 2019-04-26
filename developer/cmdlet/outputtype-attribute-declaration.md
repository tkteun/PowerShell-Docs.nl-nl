---
title: OutputType kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067600"
---
# <a name="outputtype-attribute-declaration"></a>Declaratie van het kenmerk OutputType

De `OutputType` kenmerk wordt de .NET Framework-typen die wordt geretourneerd door een cmdlet, een functie of een script.

## <a name="syntax"></a>Syntaxis

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

Type (`string[]` of `Type[]`) vereist. Hiermee geeft u de typen die zijn geretourneerd door de cmdlet-functie of het script.

ParameterSetName (string[]) Optional. Hiermee geeft u de parametersets die resulteren in de opgegeven typen in de `type` parameter.

providerCmdlet optioneel. Hiermee geeft u de provider-cmdlet die wordt geretourneerd van de typen die zijn opgegeven de `type` parameter.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
