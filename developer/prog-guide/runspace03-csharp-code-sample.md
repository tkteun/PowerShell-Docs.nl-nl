---
title: RunSpace03 (C#)-code voorbeeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848025"
---
# <a name="runspace03-c-code-sample"></a>Runspace03-codevoorbeeld (C#)

Dit is de C# bron code voor de console toepassing die wordt beschreven in een console toepassing maken die een opgegeven script uitvoert. In dit voor beeld wordt de klasse [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) gebruikt om een script uit te voeren waarmee proces gegevens worden opgehaald met behulp van de lijst met proces namen die in het script zijn door gegeven. Hierin ziet u hoe invoer objecten worden door gegeven aan een script en hoe fout objecten worden opgehaald, evenals de uitvoer objecten.

> [!NOTE]
> U kunt het C# bron bestand (runspace03.cs) voor dit voor beeld downloaden met behulp van de micro soft Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3,0 runtime-onderdelen. Zie [Windows Power Shell installeren en de Windows Power shell-SDK downloaden](/powershell/developer/installing-the-windows-powershell-sdk)voor instructies voor het downloaden.
> De gedownloade bron bestanden zijn beschikbaar in de  **\<Power shell-voor beelden >** Directory.

## <a name="code-sample"></a>Code voorbeeld

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Zie ook

[Hand leiding voor Windows Power shell-programmeurs](./windows-powershell-programmer-s-guide.md)

[Windows Power shell SDK](../windows-powershell-reference.md)