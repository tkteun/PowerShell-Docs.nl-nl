---
title: Kenmerken in cmdlet-code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359463"
---
# <a name="attributes-in-cmdlet-code"></a>Kenmerken in de cmdlet-code

Als u de algemene functionaliteit van Windows Power shell wilt gebruiken, worden de klassen en open bare eigenschappen die in de cmdlet-code zijn gedefinieerd, voorzien van kenmerken. De volgende klassen definitie maakt bijvoorbeeld gebruik van het cmdlet-kenmerk om de Microsoft .NET Framework-klasse te identificeren waarin de **Get-proc-** cmdlet wordt geïmplementeerd. (Deze cmdlet wordt gebruikt als voor beeld in dit document en is vergelijkbaar met de `Get-Process` cmdlet van Windows Power shell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Deze kenmerken worden beschouwd als meta gegevens omdat hun implementatie gescheiden is van de implementatie van de cmdlet-code. Wanneer de Windows Power shell-runtime de cmdlet uitvoert, herkent deze de kenmerken en voert vervolgens de juiste actie uit voor elk kenmerk.

Hoewel het mogelijk is om uw eigen versie van de functionaliteit van deze kenmerken te implementeren, maakt een goed ontwerp van de cmdlet gebruik van deze algemene functies.

Zie [kenmerk typen](./attribute-types.md)voor meer informatie over de verschillende kenmerken die kunnen worden gedeclareerd in de-cmdlets.

## <a name="see-also"></a>Zie ook

[Kenmerk typen](./attribute-types.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
