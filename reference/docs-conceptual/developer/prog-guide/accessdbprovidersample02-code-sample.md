---
title: Voor beeld van AccessDbProviderSample02-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416246"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDBProviderSample02-codevoorbeeld

De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md). Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.

> [!NOTE]
> U kunt het C# bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
>
> De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.
>
> Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

## <a name="code-sample"></a>Code voorbeeld

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
