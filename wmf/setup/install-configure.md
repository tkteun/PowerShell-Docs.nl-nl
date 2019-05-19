---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: keithb
title: Installeren en configureren van WMF 5.1
ms.openlocfilehash: cb223844c2a214846e7206bcb476fac9154fda4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856145"
---
# <a name="install-and-configure-wmf-51"></a>Installeren en configureren van WMF 5.1

> [!IMPORTANT]
> WMF 5.0 wordt vervangen door WMF 5.1. Gebruikers met WMF 5.0 moeten upgraden naar WMF 5.1 om ondersteuning te ontvangen.
> **WMF 5.1 vereist .NET Framework 4.5.2** (of hoger). Installatie wordt voltooid, maar de belangrijkste functies mislukken als .NET 4.5.2 (of hoger) is niet geïnstalleerd.

## <a name="download-and-install-the-wmf-51-package"></a>Download en installeer het pakket WMF 5.1

Download het WMF 5.1-pakket voor het besturingssysteem en de architectuur die u installeren wilt op:

| Besturingssysteem       | Vereisten           | Pakket-koppelingen                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- Preview-versie van WMF 5.1 moet worden verwijderd voordat de installatie van WMF 5.1 RTM.
- WMF 5.1 kan rechtstreeks via WMF 5.0 of WMF 4.0 worden geïnstalleerd.
- Het is **niet vereist** WMF 4.0 installeren voordat u WMF 5.1 installeert op Windows 7 en Windows Server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>WMF 5.1 voor Windows Server 2008 R2 en Windows 7 installeren

> [!NOTE]
> Installatie-instructies voor Windows Server 2008 R2 en Windows 7 zijn gewijzigd en verschillen van de instructies voor de andere pakketten. Installatie-instructies voor Windows Server 2012 R2, Windows Server 2012 en Windows 8.1 staan hieronder.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>WMF 5.1 installeren op Windows Server 2008 R2 en Windows 7

1. Navigeer naar de map waarin u het ZIP-bestand hebt gedownload.

2. Met de rechtermuisknop op het ZIP-bestand en selecteer 'Ophalen van alle...'. Het ZIP-bestand bevat bestanden 2: een MSU- en het scriptbestand voor installatie-WMF5.1.PS1. Zodra u het ZIP-bestand hebt uitgepakt, kunt u de inhoud kopiëren naar een machine met Windows 7 of Windows Server 2008 R2.

3. Nadat de inhoud van het ZIP-bestand uitpakken, open PowerShell als beheerder en navigeer naar de map met de inhoud van het ZIP-bestand.

4. Het script Install-Wmf5.1.ps1 uitvoeren in die map en volg de instructies. Dit script wordt Controleer de vereisten op de lokale computer en WMF 5.1 installeren als de vereisten wordt voldaan. De vereisten worden hieronder vermeld.

   Installatie-WMF5.1.ps1 bevat de volgende parameters om de automatisering van de installatie op Windows Server 2008 R2 en Windows 7:

   - AcceptEula: Als deze parameter opgenomen is, wordt de gebruiksrechtovereenkomst wordt automatisch geaccepteerd en worden niet weergegeven.
   - AllowRestart: Deze parameter kan alleen worden gebruikt als AcceptEula is opgegeven. Als deze parameter opgenomen is en een moet opnieuw opgestart worden na de installatie van WMF 5.1, gebeurt het opnieuw opstarten zonder tussenkomst van onmiddellijk nadat de installatie is voltooid.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>WMF 5.1 vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1

Installatie van WMF 5.1 op Windows Server 2008 R2 SP1 of Windows 7 SP1, is het volgende vereist:

- Meest recente servicepack moet worden geïnstalleerd.
- WMF 3.0 **moet niet** worden geïnstalleerd. WMF 5.1 installeren via WMF 3.0 zal leiden tot verlies van de PSModulePath, wat leiden andere toepassingen tot kan mislukken. Voor de installatie van WMF 5.1, een van beide ongedaan maken-Installeer WMF 3.0, moet u of de PSModulePath opslaan en vervolgens handmatig herstellen nadat WMF 5.1-installatie voltooid is.
- WMF 5.1 vereist ten minste [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  U kunt Microsoft .NET Framework 4.5.2 installeren door de instructies op de downloadlocatie.

## <a name="winrm-dependency"></a>WinRM Dependency

Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer `Set-WSManQuickConfig`, in een Windows PowerShell met verhoogde bevoegdheden om in te schakelen WinRM-sessie.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>WMF 5.1 installeren voor Windows Server 2012 R2, WindowsServer 2012 en Windows 8.1

### <a name="install-from-windows-file-explorer"></a>Installeren in Windows Verkenner

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.
2. Dubbelklik op de MSU uit te voeren.

### <a name="installing-from-the-command-prompt"></a>Installeren vanuit de opdrachtprompt

1. Na het downloaden van het juiste pakket voor de architectuur van de computer, open een opdrachtpromptvenster met verhoogde gebruikersrechten (als Administrator uitvoeren). Op de Server Core-installatieopties van Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 SP1, opdrachtprompt standaard geopend met verhoogde gebruikersrechten.
2. Wijzig de mappen in de map waarin u hebt gedownload of gekopieerd van het installatiepakket van WMF 5.1.
3. Voer een van de volgende opdrachten:
   - Voer op de computers waarop Windows Server 2012 R2 of Windows 8.1 x64, `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Voer op de computers waarop Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`.
   - Voer op de computers waarop Windows 8.1 x86, `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> De installatie van WMF 5.1 moeten opnieuw worden opgestart. Met behulp van de `/quiet` optie wordt het systeem zonder waarschuwing opnieuw. Gebruik de `/norestart` optie om te voorkomen dat opnieuw wordt opgestart. WMF 5.1 wordt echter niet worden geïnstalleerd totdat u opnieuw hebt opgestart.
