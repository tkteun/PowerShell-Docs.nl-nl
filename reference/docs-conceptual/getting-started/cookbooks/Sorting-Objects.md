---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objecten sorteren
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a>Objecten sorteren
We kunnen ordenen weergegeven gegevens om het gemakkelijker om te scannen met de **Sort-Object** cmdlet. **Sort-Object** wordt de naam van een of meer eigenschappen om te sorteren op en retourneert gegevens die zijn gesorteerd op basis van de waarden van deze eigenschappen.

U kunt het probleem van de aanbieding Win32_SystemDriver exemplaren. Als we sorteren wilt op **status** en vervolgens op **naam**, we kunt dit doen door te typen:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Hoewel dit een langdurige weergeven, kunt u de items zien met de dezelfde status gegroepeerd:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

U kunt de objecten ook in omgekeerde volgorde sorteren door op te geven de **aflopend** parameter. Hiermee wordt de sorteervolgorde zodat namen in omgekeerde alfabetische volgorde worden gesorteerd en getallen worden gesorteerd in aflopende grootte.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

