---
ms.date: 06/10/2020
title: WMF 5.1 installeren en configureren
description: In dit artikel wordt beschreven hoe u WMF 5,1 en de bijbehorende vereisten installeert.
ms.openlocfilehash: 0e076bfab684b6c83d62d236eea3bbd7ab2ad411
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660836"
---
# <a name="install-and-configure-wmf-51"></a>WMF 5,1 installeren en configureren

> [!IMPORTANT]
> WMF 5,0 is vervangen door WMF 5,1. Gebruikers met WMF 5,0 moeten een upgrade uitvoeren naar WMF 5,1 om ondersteuning te krijgen.
> Voor **WMF 5,1 is .NET Framework 4.5.2** (of hoger) vereist. De installatie wordt voltooid, maar de belangrijkste functies mislukken als .NET 4.5.2 (of hoger) niet is geïnstalleerd.

## <a name="download-and-install-the-wmf-51-package"></a>Het WMF 5,1-pakket downloaden en installeren

Down load het WMF 5,1-pakket voor het besturings systeem en de architectuur waarop u het wilt installeren:

| Besturingssysteem       | Vereisten           | Pakket koppelingen                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win 8.1 AndW2K12R2-KB3191564-x64. MSU][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64. MSU][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [win 8.1 andw2k12r2-kb3191564-x64. MSU][]</br>**x86:** [win 8.1-kb3191564-x86. MSU][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64. MSU]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win 8.1-KB3191564-x86. MSU]: https://go.microsoft.com/fwlink/?linkid=839521
[Win 8.1 AndW2K12R2-KB3191564-x64. MSU]: https://go.microsoft.com/fwlink/?linkid=839516

- De preview-versie van WMF 5,1 moet worden verwijderd voordat u WMF 5,1 RTM installeert.
- WMF 5,1 kan rechtstreeks via WMF 5,0 of WMF 4,0 worden geïnstalleerd.
- Het is **niet vereist** om WMF 4,0 te installeren voordat u WMF 5,1 installeert op Windows 7 en windows server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>WMF 5,1 installeren voor Windows Server 2008 R2 en Windows 7

> [!NOTE]
> Installatie-instructies voor Windows Server 2008 R2 en Windows 7 zijn gewijzigd en verschillen van de instructies voor de andere pakketten. Installatie-instructies voor Windows Server 2012 R2, Windows Server 2012 en Windows 8,1 vindt u hieronder.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>WMF 5,1-vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1

Voor de installatie van WMF 5,1 op Windows Server 2008 R2 SP1 of Windows 7 SP1 is het volgende vereist:

- Het meest recente Service Pack moet zijn geïnstalleerd.
- WMF 3,0 **moet niet** zijn geïnstalleerd. Het installeren van WMF 5,1 via WMF 3,0 resulteert in het verlies van de **PSModulePath** ( `$env:PSModulePath` ), wat kan leiden tot het mislukken van andere toepassingen. Voordat u WMF 5,1 installeert, moet u WMF 3,0 verwijderen of de **PSModulePath** opslaan en deze vervolgens hand matig herstellen nadat de installatie van WMF 5,1 is voltooid.
- Voor WMF 5,1 is ten minste [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)vereist. U kunt Microsoft .NET Framework 4.5.2 installeren door de instructies op de download locatie te volgen.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>WMF 5,1 installeren op Windows Server 2008 R2 en Windows 7

1. Navigeer naar de map waarin u het ZIP-bestand hebt gedownload.

1. Klik met de rechter muisknop op het ZIP-bestand en selecteer **Alles uitpakken...** . Het ZIP-bestand bevat twee bestanden: een MSU en het `Install-WMF5.1.ps1` script bestand. Zodra u het ZIP-bestand hebt uitgepakt, kunt u de inhoud kopiëren naar een computer met Windows 7 of Windows Server 2008 R2.

1. Nadat u de inhoud van het ZIP-bestand hebt uitgepakt, opent u Power shell als beheerder en navigeert u naar de map met de inhoud van het ZIP-bestand.

1. Voer het `Install-WMF5.1.ps1` script uit in die map en volg de instructies. Met dit script worden de vereisten op de lokale computer gecontroleerd en wordt WMF 5,1 geïnstalleerd als aan de vereisten is voldaan. De vereisten worden hieronder weer gegeven.

   `Install-WMF5.1.ps1` neemt de volgende para meters op om de installatie van Windows Server 2008 R2 en Windows 7 te vereenvoudigen:

   - **AcceptEula** : als deze para meter wordt opgenomen, wordt de gebruiksrecht overeenkomst automatisch geaccepteerd en wordt deze niet weer gegeven.
   - **AllowRestart** : deze para meter kan alleen worden gebruikt als AcceptEula is opgegeven. Als deze para meter is opgenomen en de computer opnieuw moet worden opgestart na de installatie van de WMF 5,1, wordt de computer opnieuw opgestart zonder dat u onmiddellijk wordt gevraagd of de installatie is voltooid.

## <a name="winrm-dependency"></a>WinRM-afhankelijkheid

Windows Power shell desired state Configuration (DSC) is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer `Set-WSManQuickConfig` uit in een Windows Power shell-sessie met verhoogde bevoegdheden om WinRM in te scha kelen.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>WMF 5,1 installeren voor Windows Server 2012 R2, Windows Server 2012 en Windows 8,1

### <a name="install-from-windows-file-explorer"></a>Installeren vanuit Windows Verkenner

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.
1. Dubbel klik op de MSU om deze uit te voeren.

### <a name="installing-from-the-command-prompt"></a>Installeren vanaf de opdracht prompt

1. Nadat u het juiste pakket voor de architectuur van de computer hebt gedownload, opent u een opdracht prompt venster met verhoogde gebruikers rechten (als administrator uitvoeren). Op de Server Core-installatie opties van Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 SP1 wordt opdracht prompt standaard geopend met verhoogde gebruikers rechten.
1. Wijzig de mappen in de map waarin u het WMF 5,1-installatie pakket hebt gedownload of gekopieerd.
1. Voer een van de volgende opdrachten uit:
   - Voer uit op computers met Windows Server 2012 R2 of Windows 8,1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart` .
   - Voer uit op computers met Windows Server 2012 `W2K12-KB3191565-x64.msu /quiet /norestart` .
   - Voer uit op computers met Windows 8,1 x86 `Win8.1-KB3191564-x86.msu /quiet /norestart` .

   > [!NOTE]
   > Voor het installeren van WMF 5,1 moet opnieuw worden opgestart. Als u de `/quiet` optie alleen gebruikt, wordt het systeem zonder waarschuwing opnieuw opgestart. Gebruik de `/norestart` optie om het opnieuw opstarten te voor komen. WMF 5,1 wordt echter pas geïnstalleerd nadat u de computer opnieuw hebt opgestart.
