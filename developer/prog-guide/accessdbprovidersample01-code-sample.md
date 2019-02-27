---
title: Codevoorbeeld AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849376"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01-codevoorbeeld

De volgende code toont de uitvoering van de Windows PowerShell-provider wordt beschreven in [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). Deze implementatie biedt methoden voor het starten en stoppen van de provider en hoewel geen een manier toegang tot een gegevensarchief biedt of als u wilt ophalen of instellen van de gegevens in het gegevensarchief, biedt de essentiële functionaliteit die is vereist voor alle providers.

> [!NOTE]
> U kunt downloaden de C# bronbestand (AccessDBSampleProvider01.cs) voor deze provider met behulp van Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen. Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.
>
> Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell-programmeergids](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)