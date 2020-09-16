---
title: Voor beeld van AccessDbProviderSample02-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ca7674ba5cff601394af4df20f0dda8794c14d22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784806"
---
# <a name="accessdbprovidersample02-code-sample"></a>AccessDBProviderSample02-codevoorbeeld

De volgende code toont de implementatie van de Windows Power shell-provider die wordt beschreven in [een Windows Power shell-schijf provider maken](./creating-a-windows-powershell-drive-provider.md).
Deze implementatie maakt een pad, maakt verbinding met een Access-Data Base en verwijdert vervolgens het station.

> [!NOTE]
> U kunt het C#-bron bestand (AccessDBSampleProvider02.cs) voor deze provider downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden bevinden zich in de **\<PowerShell Samples>** map. Zie [uw Windows Power shell-provider ontwerpen](./designing-your-windows-powershell-provider.md)voor meer informatie over andere implementaties van Windows Power shell-providers.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a>Zie ook

[Handleiding voor Windows PowerShell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
