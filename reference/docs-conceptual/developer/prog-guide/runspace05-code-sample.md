---
title: Voor beeld van RunSpace05-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 4d9a2db76fe69a8509d33a22124f5f952b1d3c80
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978301"
---
# <a name="runspace05-code-sample"></a>Runspace05-codevoorbeeld

Dit is de bron code voor het Runspace05-voor beeld dat wordt beschreven in [een runs Pace configureren met behulp van RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).
Dit voor beeld laat zien hoe u de runs Pace-configuratie gegevens maakt, een runs Pace maakt, een pijp lijn maakt met één opdracht en vervolgens de pijp lijn uitvoert. De opdracht die wordt uitgevoerd, is de `Get-Process`-cmdlet.

> [!NOTE]
> U kunt het C# bron bestand (runspace05.cs) downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/scripting/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden zijn beschikbaar in de **\<Power shell-voor beelden >** map.

## <a name="code-sample"></a>Code voorbeeld

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
