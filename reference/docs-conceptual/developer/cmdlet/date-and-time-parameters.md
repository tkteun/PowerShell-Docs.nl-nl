---
title: Datum-en tijd parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359388"
---
# <a name="date-and-time-parameters"></a>Datum- en tijdparameters

De volgende tabel bevat de aanbevolen namen en functionaliteit voor para meters die datum-en tijd gegevens verwerken. Datum-en tijd parameters worden meestal gebruikt om vast te leggen wanneer iets wordt gemaakt of geopend.

|Parameter|Functionaliteit|
|---|---|
|**Gebruikte**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op de resources die zijn geopend op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **created** en **Modified** niet worden opgegeven.|
|**After**<br>Gegevens type: DateTime|Implementeer deze para meter om de datum en tijd op te geven waarna de cmdlet is gebruikt. De para meter **After** kan alleen worden gebruikt als de cmdlet een **toegang**, **gemaakt**of **gewijzigd** heeft. En de para meter moet worden ingesteld op **True** wanneer de cmdlet wordt aangeroepen.|
|**Bij**<br>Gegevens type: DateTime|Implementeer deze para meter om de datum en tijd op te geven waarna de cmdlet is gebruikt. De para meter **before** werkt alleen als de cmdlet een **toegang**, **gemaakt**of **gewijzigd** heeft. En de para meter moet worden ingesteld op **True** wanneer de cmdlet wordt aangeroepen.|
|**Toegevoegd**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op de resources die zijn gemaakt op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **toegankelijk** en **gewijzigd** niet worden opgegeven.|
|**Letters**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de resource term precies overeenkomt met de resource naam wanneer deze is opgegeven. Als de para meter niet is opgegeven, moeten de resource term en naam niet exact overeenkomen.|
|**Aangebracht**<br>Gegevens type: DateTime|Implementeer deze para meter zodat wanneer deze is opgegeven, de cmdlet wordt uitgevoerd op resources die zijn gewijzigd op basis van de datum en tijd die zijn opgegeven met de para meters **voor** en **na** . Als deze para meter is opgegeven, moeten de para meters **toegankelijk** en **gemaakt** niet worden opgegeven.|
## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
