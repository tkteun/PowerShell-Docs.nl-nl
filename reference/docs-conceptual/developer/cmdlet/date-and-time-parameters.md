---
title: Datum-en tijd parameters | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f1b2bb3b3da2b73860298e36d88502bfd67c5b22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774657"
---
# <a name="date-and-time-parameters"></a>Datum- en tijdparameters

De volgende tabel bevat de aanbevolen namen en functionaliteit voor para meters die datum-en tijd gegevens verwerken. Datum-en tijd parameters worden meestal gebruikt om vast te leggen wanneer iets wordt gemaakt of geopend.

|Parameter|Functionaliteit|
|---|---|
|**Gebruikte**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op de resources die zijn geopend op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **created** en **Modified** niet worden opgegeven.|
|**Na**<br>Gegevens type: DateTime|Implementeer deze para meter om de datum en tijd op te geven waarna de cmdlet is gebruikt. De para meter **After** kan alleen worden gebruikt als de cmdlet een **toegang**, **gemaakt**of **gewijzigd** heeft. En de para meter moet worden ingesteld op **True** wanneer de cmdlet wordt aangeroepen.|
|**Voor**<br>Gegevens type: DateTime|Implementeer deze para meter om de datum en tijd op te geven waarna de cmdlet is gebruikt. De para meter **before** werkt alleen als de cmdlet een **toegang**, **gemaakt**of **gewijzigd** heeft. En de para meter moet worden ingesteld op **True** wanneer de cmdlet wordt aangeroepen.|
|**Aangemaakt**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op de resources die zijn gemaakt op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **toegankelijk** en **gewijzigd** niet worden opgegeven.|
|**Letters**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de resource term precies overeenkomt met de resource naam wanneer deze is opgegeven. Als de para meter niet is opgegeven, moeten de resource term en naam niet exact overeenkomen.|
|**Aangebracht**<br>Gegevens type: DateTime|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op resources die zijn gewijzigd op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **toegankelijk** en **gemaakt** niet worden opgegeven.|
## <a name="see-also"></a>Zie ook

[Cmdlet-parameters](./cmdlet-parameters.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
