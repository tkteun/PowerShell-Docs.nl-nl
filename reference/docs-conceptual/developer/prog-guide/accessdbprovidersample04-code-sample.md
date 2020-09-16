---
title: Voor beeld van AccessDbProviderSample04-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 05509c5b36475bcd3f91c9ab7413974994d668d6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787271"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDBProviderSample04-codevoorbeeld

De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-container provider maken](./creating-a-windows-powershell-container-provider.md).
Deze provider werkt op gegevens archieven met meerdere lagen. Voor dit type gegevens archief bevat het hoogste niveau van de Store de hoofd items en elk volgend niveau wordt een knoop punt van onderliggende items genoemd. Door de gebruiker toe te staan om deze onderliggende knoop punten te gebruiken, kan een gebruiker hiërarchisch communiceren via het gegevens archief.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)
