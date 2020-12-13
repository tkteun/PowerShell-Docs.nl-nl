---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04-codevoorbeeld
description: AccessDBProviderSample04-codevoorbeeld
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647560"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDBProviderSample04-codevoorbeeld

De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).
Deze provider werkt op gegevens archieven met meerdere lagen. Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd. Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
