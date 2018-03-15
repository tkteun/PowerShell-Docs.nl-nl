---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 510e1baa2933932cfd4c3bcb4e0973f3eb8095f3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="system-requirements"></a>Systeemvereisten

- Installeer de meest recente Windows-updates voor de installatie van WMF 5.0 RTM.
- U kunt WMF 5.0 RTM installeren alleen op de volgende besturingssystemen:

    | Besturingssysteem       | Edities         | Vereisten        |  Pakket koppelingen |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Alles, behalve IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) en [.NET Framework 4.5 of hoger](https://msdn.microsoft.com/library/5a4x27ek.aspx) zijn geïnstalleerd| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Alles | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) en [.NET Framework 4.5 of hoger](https://msdn.microsoft.com/library/5a4x27ek.aspx) zijn geïnstalleerd | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Installatie-instructies

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Voor het installeren van WMF 5.0 vanuit Windows Verkenner (of Windows Verkenner):

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.

2. Dubbelklik op de MSU uit te voeren.

### <a name="to-install-wmf-50-from-command-prompt"></a>WMF 5.0 installeren vanaf de opdrachtprompt:

1. Na het downloaden van het juiste pakket voor de architectuur van uw computer, open een opdrachtpromptvenster met verhoogde gebruikersrechten (als Administrator uitvoeren). Op de Server Core-installatieopties van Windows Server 2012 R2 of Windows Server 2012 of Windows Server 2008 R2 SP1, opdrachtprompt standaard geopend met verhoogde gebruikersrechten.

2. Wijzig de mappen in de map waarin u hebt gedownload of gekopieerd van het installatiepakket WMF 5.0.

3. Voer een van de volgende opdrachten:
    - Voer op de computers waarop Windows Server 2012 R2 of Windows 8.1 x64, **Win8.1AndW2K12R2-KB3134758-x64.msu quiet**.
    - Voer op de computers waarop Windows Server 2012, **W2K12-KB3134759-x64.msu quiet**.
    - Voer op de computers waarop Windows Server 2008 R2 SP1 of Windows 7 SP1 x 64, **Win7AndW2K8R2-KB3134760-x64.msu quiet**.
    - Voer op de computers waarop Windows 8.1 x86, **Win8.1-KB3134758-x86.msu quiet**.
    - Voer op de computers waarop Windows 7 SP1 x 86, **Win7-KB3134760-x86.msu quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Van aanvullende Installatieopmerkingen voor Windows Server 2008 R2 SP1 en Windows 7 SP1:

Zorg ervoor dat de volgende vereisten wordt voldaan:
- Meest recente servicepack is geïnstalleerd.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) is geïnstalleerd.
- [.NET framework 4.5 of hoger](https://msdn.microsoft.com/library/5a4x27ek.aspx) is geïnstalleerd.

**WMF 4.0 Dependency**

Windows Server 2008 R2 SP1 en Windows 7 SP1 systemen hebben ingebouwde PowerShell 2.0, WinRM en WMI. WMF 3.0 en WMF 4.0-pakketten, die deze ingebouwde onderdelen bijwerkt, zijn na de release van Windows Server 2008 R2 SP1 en Windows 7 SP1 uitgebracht. Pakketten installeren/verwijderen WMF 3.0 en WMF 4.0 gesignaleerde sommige problemen in het volgende upgradepad:

- Built-in --> WMF 4.0
- Built-in --> WMF 3.0 --> WMF4.0. 

We al deze problemen opgelost in WMF 4.0-pakketten. Er is daarom een vereiste van WMF 4.0 voor het installeren van WMF 5.0 op Windows Server 2008 R2 SP1 en Windows 7 SP1. Hieronder worden de specifieke problemen die optreden kunnen als u WMF 4.0 niet vóór de upgrade naar WMF 5.0 installeert:

- Logboek met doorgestuurde gebeurtenissen is niet beschikbaar en EventCollector logboek is niet zichtbaar in Logboeken na het verwijderen van WMF 3.0 of WMF 5.0 (zonder de vereiste WMF 4.0 is geïnstalleerd) in Windows 7 SP1 en Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- Aanpassing *PSModulePath* omgevingsvariabele opgehaald opnieuw ingesteld op standaardwaarde wanneer u rechtstreeks vanuit de ingebouwde PowerShell 2.0 een naar WMF 5.0 upgrade ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) of van WMF 3.0 naar WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) in Windows 7 SP1 en Windows Server 2008 R2 SP1.

**WinRM-afhankelijkheid**

Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 SP1 en Windows 7 SP1. Inschakelen van WinRM, verhoogde in een Windows PowerShell-sessie uitvoeren **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Instructies voor het verwijderen

### <a name="using-command-prompt"></a>Vanaf een opdrachtprompt

1.  Open **opdrachtprompt.**

2.  Voer de [Windows Update zelfstandige Launcher](https://support.microsoft.com/en-us/kb/934307) zoals hieronder wordt weergegeven:

Op Windows Server 2012 R2 en Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
On Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
Op Windows Server 2008 R2 SP1 en Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Via het Configuratiescherm

1.  Open **het Configuratiescherm.**

2.  Open **programma's**, open vervolgens **een programma verwijderen.**

3.  Klik op **geïnstalleerde updates weergeven.**

4.  Selecteer **Windows Management Framework 5.0** uit de lijst met geïnstalleerde updates. Dit komt overeen met *KB3134758*, *KB3134759*, of *KB3134760*. Klik op **verwijderen.**

