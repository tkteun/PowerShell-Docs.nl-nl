---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
contributor: keithb
title: Installeren en configureren van WMF 5.1
ms.openlocfilehash: 74c19d2eb04b77b1e2b1c8d8977f9b4db6e94e4f
ms.sourcegitcommit: 9910675e8758042b5949c99b381a926d2b4e8c21
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-wmf-51"></a>Installeren en configureren van WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Download en installeer het pakket WMF 5.1

Download het pakket WMF 5.1 voor het besturingssysteem en de architectuur die u installeren wilt op:

| Besturingssysteem       | Vereisten       | Pakket koppelingen             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012    | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-voor x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86:** [Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64:** [Win7AndW2K8R2-KB3191566-voor x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86:** [Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>WMF 5.1 voor Windows Server 2008 R2 en Windows 7 installeren

> **Opmerking:** installatie-instructies voor Windows Server 2008 R2 en Windows 7 zijn gewijzigd en verschillen van de instructies voor de andere pakketten. Installatie-instructies voor Windows Server 2012 R2, Windows Server 2012 en Windows 8.1 zijn hieronder.

**Installeren van WMF 5.1 op Windows Server 2008 R2 en Windows 7**

1. Navigeer naar de map waarin u het ZIP-bestand hebt gedownload. 

2. Met de rechtermuisknop op het ZIP-bestand en selecteer 'Pak alle...'. Het ZIP-bestand bevat 2 bestanden: een MSU- en het scriptbestand voor installatie WMF5.1.PS1. Zodra u het ZIP-bestand hebt uitgepakt, kunt u de inhoud kopiëren naar een machine met Windows 7 of Windows Server 2008 R2.  

3. Nadat u hebt het ZIP-bestand uitgepakt bestand inhoud, opent u PowerShell als beheerder en navigeer naar de map met de  
de inhoud van het ZIP-bestand. 

4. Het script Install-Wmf5.1.ps1 uitvoeren in die map en volg de instructies. Dit script wordt de vereisten op de lokale computer en WMF 5.1 installeren als de vereisten is voldaan. De vereisten worden hieronder vermeld. 

Installatie WMF5.1.ps1 bevat de volgende parameters te vereenvoudigen voor het automatiseren van de installatie op Windows Server 2008 R2 en Windows 7:

- AcceptEula: Als deze parameter opgenomen is, de gebruiksrechtovereenkomst automatisch worden geaccepteerd en worden niet weergegeven.
- AllowRestart: Deze parameter kan alleen worden gebruikt als AcceptEula is opgegeven. Als deze parameter opgenomen is en moet opgestart worden na het installeren van WMF 5.1, gebeurt het opnieuw opstarten zonder onmiddellijk nadat de installatie is voltooid. 

**WMF 5.1 vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1**

Installatie van WMF 5.1 op Windows Server 2008 R2 SP1 of Windows 7 SP1 is het volgende vereist:
- Meest recente servicepack moet worden geïnstalleerd.
- WMF 3.0 **moet niet** worden geïnstalleerd. Het installeren van WMF 5.1 via WMF 3.0 leidt tot het verlies van de PSModulePath, wat leiden andere toepassingen tot kan mislukken. Voordat u WMF 5.1 installeert, u moet beide WMF 3.0 van het verwijderen of opslaan van de PSModulePath en vervolgens handmatig herstellen nadat WMF 5.1-installatie voltooid is. 
- WMF 5.1 vereist ten minste [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
U kunt Microsoft .NET Framework 4.5.2 installeren door de instructies op de downloadlocatie.

**WinRM-afhankelijkheid** 

Windows PowerShell Desired State Configuration (DSC), is afhankelijk van WinRM. WinRM is niet standaard ingeschakeld op Windows Server 2008 R2 en Windows 7. Voer `Set-WSManQuickConfig`, in een Windows PowerShell met verhoogde bevoegdheden voor het inschakelen van de WinRM-sessie.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>WMF 5.1 voor Windows Server 2012 R2, WindowsServer 2012 en Windows 8.1 installeren
**Installeren van Windows Verkenner (of Windows Verkenner in Windows Server 2012 R2 of Windows 8.1)**

1. Navigeer naar de map waarin u het MSU-bestand hebt gedownload.

2. Dubbelklik op de MSU uit te voeren.

**Installatie vanaf de opdrachtprompt**

1. Na het downloaden van het juiste pakket voor de architectuur van uw computer, open een opdrachtpromptvenster met verhoogde gebruikersrechten (als Administrator uitvoeren). Op de Server Core-installatieopties van Windows Server 2012 R2, Windows Server 2012 of Windows Server 2008 R2 SP1, opdrachtprompt standaard geopend met verhoogde gebruikersrechten.

2. Wijzig de mappen in de map waarin u hebt gedownload of het installatiepakket WMF 5.1 gekopieerd.

3. Voer een van de volgende opdrachten:
    - Voer op de computers waarop Windows Server 2012 R2 of Windows 8.1 x64, `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
    - Voer op de computers waarop Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`.
    - Voer op de computers waarop Windows 8.1 x86, `Win8.1-KB3191564-x86.msu /quiet`.
    
