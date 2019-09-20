---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: keithb
title: WMF 5.1 installeren en configureren
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145094"
---
# <a name="install-and-configure-wmf-51"></a>WMF 5,1 installeren en configureren

> [!IMPORTANT]
> WMF 5,0 is vervangen door WMF 5,1. Gebruikers met WMF 5,0 moeten een upgrade uitvoeren naar WMF 5,1 om ondersteuning te krijgen.
> Voor **WMF 5,1 is .NET Framework 4.5.2 vereist** (of hoger). De installatie wordt voltooid, maar de belangrijkste functies mislukken als .NET 4.5.2 (of hoger) niet is geïnstalleerd.

## <a name="download-and-install-the-wmf-51-package"></a>Het WMF 5,1-pakket downloaden en installeren

Down load het WMF 5,1-pakket voor het besturings systeem en de architectuur waarop u het wilt installeren:

| Besturingssysteem       | Vereisten           | Pakket koppelingen                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x86** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x86** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- De preview-versie van WMF 5,1 moet worden verwijderd voordat u WMF 5,1 RTM installeert.
- WMF 5,1 kan rechtstreeks via WMF 5,0 of WMF 4,0 worden geïnstalleerd.
- Het is **niet vereist** om WMF 4,0 te installeren voordat u WMF 5,1 installeert op Windows 7 en windows server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>WMF 5,1 installeren voor Windows Server 2008 R2 en Windows 7

> [!NOTE]
> Installatie-instructies voor Windows Server 2008 R2 en Windows 7 zijn gewijzigd en verschillen van de instructies voor de andere pakketten. Installatie-instructies voor Windows Server 2012 R2, Windows Server 2012 en Windows 8,1 vindt u hieronder.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>WMF 5,1-vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1

Voor de installatie van WMF 5,1 op Windows Server 2008 R2 SP1 of Windows 7 SP1 is het volgende vereist:

- Het meest recente Service Pack moet zijn geïnstalleerd.
- WMF 3,0 **moet niet** zijn geïnstalleerd. Het installeren van WMF 5,1 via WMF 3,0 resulteert in het verlies van de PSModulePath`$env:PSModulePath`(), wat kan leiden tot het mislukken van andere toepassingen. Voordat u WMF 5,1 installeert, moet u WMF 3,0 verwijderen of de **PSModulePath** opslaan en deze vervolgens hand matig herstellen nadat de installatie van WMF 5,1 is voltooid.
- Voor WMF 5,1 is ten minste [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)vereist.
  U kunt Microsoft .NET Framework 4.5.2 installeren door de instructies op de download locatie te volgen.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>WMF 5,1 installeren op Windows Server 2008 R2 en Windows 7

1. Navigeer naar de map waarin u het ZIP-bestand hebt gedownload.

2. Klik met de rechter muisknop op het ZIP-bestand en selecteer **Alles uitpakken...** . Het zip-bestand bevat twee bestanden: een MSU en `Install-WMF5.1.ps1` het script bestand. Zodra u het ZIP-bestand hebt uitgepakt, kunt u de inhoud kopiëren naar een computer met Windows 7 of Windows Server 2008 R2.

3. Nadat u de inhoud van het ZIP-bestand hebt uitgepakt, opent u Power shell als beheerder en navigeert u naar de map met de inhoud van het ZIP-bestand.

4. Voer het `Install-WMF5.1.ps1` script uit in die map en volg de instructies. Met dit script worden de vereisten op de lokale computer gecontroleerd en wordt WMF 5,1 geïnstalleerd als aan de vereisten is voldaan. De vereisten worden hieronder weer gegeven.

   `Install-WMF5.1.ps1`neemt de volgende para meters op om de installatie van Windows Server 2008 R2 en Windows 7 te vereenvoudigen:

   - **AcceptEula**: Als deze para meter is opgenomen, wordt de gebruiksrecht overeenkomst automatisch geaccepteerd en wordt deze niet weer gegeven.
   - **AllowRestart**: Deze para meter kan alleen worden gebruikt als AcceptEula is opgegeven. Als deze para meter is opgenomen en de computer opnieuw moet worden opgestart na de installatie van de WMF 5,1, wordt de computer opnieuw opgestart zonder dat u onmiddellijk wordt gevraagd of de installatie is voltooid.

## <a name="winrm-dependency"></a>WinRM-afhankelijkheid

Windows Power shell desired state Configuration (DSC) is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer `Set-WSManQuickConfig`uit in een Windows Power shell-sessie met verhoogde bevoegdheden om WinRM in te scha kelen.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>WMF 5,1 installeren voor Windows Server 2012 R2, Windows Server 2012 en Windows 8,1

### <a name="install-from-windows-file-explorer"></a>Installeren vanuit Windows Verkenner

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.
2. Dubbel klik op de MSU om deze uit te voeren.

### <a name="installing-from-the-command-prompt"></a>Installeren vanaf de opdracht prompt

1. Nadat u het juiste pakket voor de architectuur van de computer hebt gedownload, opent u een opdracht prompt venster met verhoogde gebruikers rechten (als administrator uitvoeren). Op de Server Core-installatie opties van Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 SP1 wordt opdracht prompt standaard geopend met verhoogde gebruikers rechten.
2. Wijzig de mappen in de map waarin u het WMF 5,1-installatie pakket hebt gedownload of gekopieerd.
3. Voer een van de volgende opdrachten uit:
   - Voer uit `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`op computers met Windows Server 2012 R2 of Windows 8,1 x64.
   - Voer uit `W2K12-KB3191565-x64.msu /quiet`op computers met Windows Server 2012.
   - Voer uit `Win8.1-KB3191564-x86.msu /quiet`op computers met Windows 8,1 x86.

> [!NOTE]
> Voor het installeren van WMF 5,1 moet opnieuw worden opgestart. Als u `/quiet` de optie gebruikt, wordt het systeem zonder waarschuwing opnieuw opgestart. Gebruik de `/norestart` optie om het opnieuw opstarten te voor komen. WMF 5,1 wordt echter pas geïnstalleerd nadat u de computer opnieuw hebt opgestart.
