---
title: Aantal para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359256"
---
# <a name="quantity-parameters"></a>Hoeveelheidsparameters

De volgende tabel bevat de aanbevolen namen en functionaliteit voor hoeveelheids parameters.

|Parameter|Functionaliteit|
|---|---|
|**Hele**<br>Gegevens type: Booleaans|Implementeer deze para meter zodanig dat `true` aangeeft dat alle resources moeten worden uitgevoerd in plaats van een standaard subset van resources. Implementeer deze para meter zodanig dat `false` een subset van de resources aangeeft.|
|**Configuration**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker het aantal items kan opgeven dat moet worden toegewezen.|
|**BlockCount**<br>Gegevens type: Int64|Implementeer deze para meter zodat de gebruiker het aantal blokken kan opgeven.|
|**Aantal**<br>Gegevens type: Int64|Implementeer deze para meter zodat de gebruiker de telling kan opgeven.|
|**Ligt**<br>Gegevens type: tref woord|Implementeer deze para meter zodat de gebruiker het bereik kan opgeven dat moet worden gebruikt.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
