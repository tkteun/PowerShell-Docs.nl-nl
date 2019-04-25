---
title: Codevoorbeeld RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081220"
---
# <a name="runspace09-code-sample"></a>Runspace09-codevoorbeeld

Hier volgt de broncode voor het voorbeeld Runspace09 die zijn beschreven [het maken van een Console-toepassing die roept een pijplijn asynchroon](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Deze voorbeeldtoepassing maakt en een runspace wordt geopend, maakt en een pijplijn asynchroon aanroept, en vervolgens maakt gebruik van pipeline-gebeurtenissen voor het asynchroon verwerken van het script. Het script dat wordt uitgevoerd door deze toepassing maakt de getallen 1 t/m 10 0,5 seconde intervallen (500 ms).

## <a name="code-sample"></a>Voorbeeld van code

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Zie ook

[Windows PowerShell SDK](../windows-powershell-reference.md)