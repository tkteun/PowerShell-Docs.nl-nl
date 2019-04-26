---
title: De datum en tijdparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068229"
---
# <a name="date-and-time-parameters"></a>Datum- en tijdparameters

De volgende tabel bevat de namen van de aanbevolen en de functionaliteit voor parameters die werken met gegevens van de datum en tijd. Datum en tijd-parameters worden meestal gebruikt om vast te leggen wanneer iets wordt gemaakt of geopend.

|Parameter|Functionaliteit|
|---|---|
|**Toegang tot**<br>Gegevenstype: SwitchParameter|Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gebruikt op basis van de datum en tijd die is opgegeven door de **voordat** en **na** parameters. Als deze parameter is opgegeven, de **gemaakt** en **gewijzigd** parameters moeten niet worden opgegeven.|
|**Na**<br>Gegevenstype: DateTime|Implementeer deze parameter om op te geven van de datum en tijd waarna de cmdlet is gebruikt. Voor de **na** parameter om te werken, de cmdlet moet ook beschikken over een **toegang**, **gemaakt**, of **gewijzigd** parameter. En deze parameter moet worden ingesteld op **waar** wanneer de cmdlet wordt aangeroepen.|
|**Voordat u**<br>Gegevenstype: DateTime|Implementeer deze parameter om op te geven van de datum en tijd waarbinnen de cmdlet is gebruikt. Voor de **voordat** parameter om te werken, de cmdlet moet ook beschikken over een **toegang**, **gemaakt**, of **gewijzigd** parameter. En deze parameter moet worden ingesteld op **waar** wanneer de cmdlet wordt aangeroepen.|
|**Gemaakt**<br>Gegevenstype: SwitchParameter|Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gemaakt op basis van de datum en tijd die is opgegeven door de **voordat** en **na** parameters. Als deze parameter is opgegeven, de **toegang** en **gewijzigd** parameters moeten niet worden opgegeven.|
|**Exacte**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat wanneer deze de termijn van de resource is opgegeven moet precies overeenkomen met de naam van de resource. Als de parameter niet is opgegeven hoeft de termijn van de resource en de naam niet precies.|
|**Gewijzigd**<br>Gegevenstype: DateTime|Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op resources die zijn gewijzigd op basis van de datum en tijd die is opgegeven door de **voordat** en **na** parameters. Als deze parameter is opgegeven, de **toegang** en **gemaakt** parameters moeten niet worden opgegeven.|
## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
