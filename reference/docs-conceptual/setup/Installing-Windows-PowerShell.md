---
ms.date: 2017-08-09
keywords: PowerShell-cmdlet, downloaden, installeren, setup, windows 10, windows 8.1, windows 8.0, windows 7
title: Windows PowerShell installeren
ms.openlocfilehash: dffb6ec11ce265ebc4e6bc91f631650e1af5868d
ms.sourcegitcommit: 05d576cf107780fa52b2db4a042816be40b00fbc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="installing-windows-powershell"></a>Windows PowerShell installeren
Windows PowerShell wordt geleverd in elke Windows, Windows 7 SP1 en Windows Server 2008 R2 SP1 vanaf standaard geïnstalleerd.

Als u geïnteresseerd in PowerShell 6 en hoger bent, moet u PowerShell Core in plaats van Windows PowerShell te installeren. Zie [PowerShell Core installeren op Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Het vinden van PowerShell in Windows 10, 8.1, 8.0 en 7

Soms zoeken PowerShell kan-console of ISE (Integrated Scripting Environment) in Windows moeilijk zijn, zoals de locatie wordt verplaatst van één versie van Windows naar de volgende.

De volgende tabellen kunt u PowerShell niet vinden in uw Windows-versie.
Alle versies die hier zijn de oorspronkelijke versie als vrijgegeven met geen updates.

### <a name="for-console"></a>Voor de Console

Versie | Locatie
-- | --
Windows 10 | Klik op pictogram linksboven lagere hoek Windows, begint te typen van PowerShell
Windows 8.1, 8.0 | Start PowerShell te typen op het startscherm.<br/>Als een waarde op het bureaublad, klikt u op links lagere hoek pictogram van Windows, begint te typen van PowerShell
Windows 7 SP1 | Klik op links lagere hoek Windows pictogram op de zoekopdracht vak begin typen PowerShell

### <a name="for-ise"></a>Voor ISE

Versie | Locatie
-- | --
Windows 10 | Klik op pictogram linksboven lagere hoek Windows, begint te typen ISE
Windows 8.1, 8.0 | Typ op het startscherm **PowerShell ISE**.<br/>Als op bureaublad, klikt u op lagere hoek Windows pictogram, typ **PowerShell ISE**
Windows 7 SP1 | Klik op links lagere hoek Windows pictogram op de zoekopdracht vak begin typen PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>Het vinden van PowerShell in Windows Server-versies

Beginnen met Windows Server 2008 R2, worden Windows-besturingssysteem geïnstalleerd zonder de grafische gebruikersinterface (GUI).
Versies van Windows Server zonder de gebruikersinterface zijn benoemde **Core** versies en edities met de gebruikersinterface zijn benoemde **bureaublad**.

### <a name="windows-server-core-editions"></a>Windows Server Core-versies

In alle edities van de Core, wanneer u zich bij de server aanmeldt krijgt u een Windows-opdrachtpromptvenster.

Type `powershell` en druk op **ENTER** PowerShell starten binnen de opdrachtpromptsessie. Type `exit` de PowerShell-sessie te beëindigen en terugkeren naar de opdrachtprompt.

### <a name="windows-server-desktop-editions"></a>Bureaublad van Windows Server-edities

In alle edities van bureaublad, klik op het pictogram links lagere hoek Windows, begint te typen van PowerShell.
Krijgt u zowel de console en de ISE-opties.

De enige uitzondering aan de bovenstaande regel is de ISE in Windows Server 2008 R2 SP1; in dit geval, klik op het pictogram links lagere hoek Windows, typ PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Het controleren van de versie van PowerShell

Als u wilt zoeken op welke versie van PowerShell die u hebt geïnstalleerd, start u een PowerShell-console (of de ISE) en type `$PSVersionTable` en druk op **ENTER**. Zoek naar de `PSVersion` waarde.

## <a name="upgrading-existing-windows-powershell"></a>Upgraden van bestaande Windows PowerShell

Het installatiepakket voor PowerShell wordt geleverd in een installatieprogramma WMF.
De versie van het installatieprogramma WMF overeenkomt met de versie van PowerShell; Er is geen zelfstandige installatieprogramma voor Windows PowerShell.

Als u wilt bijwerken van uw huidige versie van PowerShell in Windows gebruik u de volgende tabel om te vinden van het installatieprogramma voor de versie van PowerShell die u bijwerken wilt naar.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (Zie Note1)<br/>Windows Server 2016 | - | - | - | geïnstalleerd
Windows 8.1<br/>Windows Server 2012 R2 | - | geïnstalleerd | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | geïnstalleerd | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Opmerking 1**:
  >>
  >> Op de eerste release van Windows 10, met automatische updates is ingeschakeld, wordt PowerShell van versie 5.0-5.1 bijgewerkt.
  >>
  >> Als de oorspronkelijke versie van Windows 10 niet via de Windows-Updates bijgewerkt is, is de versie van PowerShell 5.0.

## <a name="need-azure-powershell"></a>Moet u Azure PowerShell

Als u zoekt **Azure PowerShell**, kan worden gestart met [overzicht van Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).

Wat u moet mogelijk anders is [installeren en configureren van Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="see-also"></a>Zie ook

- [Systeemvereisten voor Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Windows PowerShell starten](Starting-Windows-PowerShell.md)
