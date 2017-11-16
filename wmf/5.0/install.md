---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 668a5b20add58ff5e23f35d6cebddc39c64ce926
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="installation-instructions"></a>Installatie-instructies

Download het juiste pakket voor uw besturingssysteem en architectuur:

| Besturingssysteem       | Architectuur | Naam van het pakket              | 
|------------------------|--------------|---------------------------| 
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) | 
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) | 
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Voor het installeren van WMF 5.0 vanuit Windows Verkenner (of Windows Verkenner in Windows Server 2012 R2 en Windows 8.1):**

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.

2. Dubbelklik op de MSU uit te voeren.

**WMF 5.0 installeren vanaf de opdrachtprompt:** 

1. Na het downloaden van het juiste pakket voor de architectuur van uw computer, open een opdrachtpromptvenster met verhoogde gebruikersrechten (als Administrator uitvoeren). Op de Server Core-installatieopties van Windows Server 2012 R2 of Windows Server 2012 of Windows Server 2008 R2 SP1, opdrachtprompt standaard geopend met verhoogde gebruikersrechten.

2. Wijzig de mappen in de map waarin u hebt gedownload of gekopieerd van het installatiepakket WMF 5.0.

3. Voer een van de volgende opdrachten:
    - Voer op de computers waarop Windows Server 2012 R2 of Windows 8.1 x64, **Win8.1AndW2K12R2-KB3134758-x64.msu quiet**.
    - Voer op de computers waarop Windows Server 2012, **W2K12-KB3134759-x64.msu quiet**.
    - Voer op de computers waarop Windows Server 2008 R2 SP1 of Windows 7 SP1 x 64, **Win7AndW2K8R2-KB3134760-x64.msu quiet**.
    - Voer op de computers waarop Windows 8.1 x86, **Win8.1-KB3134758-x86.msu quiet**.
    - Voer op de computers waarop Windows 7 SP1 x 86, **Win7-KB3134760-x86.msu quiet**.

**Van aanvullende Installatieopmerkingen voor Windows Server 2008 SP1 en Windows 7 SP1:**

Zorg ervoor dat de volgende vereisten wordt voldaan:
- Meest recente servicepack is geïnstalleerd.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) is geïnstalleerd

*WinRM afhankelijkheid:* Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Inschakelen van WinRM, verhoogde in een Windows PowerShell-sessie uitvoeren **Set-WSManQuickConfig**.


