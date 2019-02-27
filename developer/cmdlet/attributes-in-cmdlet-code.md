---
title: Kenmerken in de Cmdlet-Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845260"
---
# <a name="attributes-in-cmdlet-code"></a>Kenmerken in de cmdlet-code

De algemene functionaliteit die is geleverd door Windows PowerShell wilt gebruiken, worden de klassen en de openbare eigenschappen die zijn gedefinieerd in de cmdlet-code voorzien van kenmerken. De volgende klassendefinitie gebruikt bijvoorbeeld de Cmdlet-kenmerk voor het identificeren van de Microsoft .NET Framework-klasse waarin de **Get-Proc** cmdlet is geïmplementeerd. (Deze cmdlet wordt gebruikt als een voorbeeld in dit document en is vergelijkbaar met de `Get-Process` geleverd door Windows PowerShell cmdlet.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Deze kenmerken worden beschouwd als van metagegevens omdat de toepassing gescheiden van de implementatie van de cmdlet-code is. Wanneer de Windows PowerShell-runtime wordt uitgevoerd van de cmdlet, herkent de kenmerken en vervolgens de juiste actie uitvoeren voor elk kenmerk.

Hoewel u wilt mogelijk voor het implementeren van uw eigen versie van de functionaliteit van deze kenmerken, een goede cmdlet-ontwerp maakt gebruik van deze algemene functionaliteit.

Zie voor meer informatie over de verschillende kenmerken die kunnen worden gedefinieerd in uw cmdlets, [kenmerktypen](./attribute-types.md).

## <a name="see-also"></a>Zie ook

[Kenmerktypen](./attribute-types.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
