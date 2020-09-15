---
title: Kenmerken in cmdlet-code | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774912"
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

[Typen kenmerken](./attribute-types.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
