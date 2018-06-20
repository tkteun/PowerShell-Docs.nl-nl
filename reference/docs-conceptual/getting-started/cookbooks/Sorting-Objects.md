---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objecten sorteren
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 272d550a67b206f9924ebe143eca2f5906c0a304
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949975"
---
# <a name="sorting-objects"></a>Objecten sorteren

We kunnen ordenen weergegeven gegevens om het gemakkelijker om te scannen met de **Sort-Object** cmdlet. **Sort-Object** wordt de naam van een of meer eigenschappen om te sorteren op en retourneert gegevens die zijn gesorteerd op basis van de waarden van deze eigenschappen.

U kunt het probleem van de aanbieding Win32_SystemDriver exemplaren. Als we sorteren wilt op **status** en vervolgens op **naam**, we kunt dit doen door te typen:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Hoewel dit een langdurige weergeven, kunt u de items zien met de dezelfde status gegroepeerd:

```output
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