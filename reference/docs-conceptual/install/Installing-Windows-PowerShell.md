---
ms.date: 08/09/2017
keywords: PowerShell, cmdlet, downloaden, installeren, instellingen, windows 10, windows 8.1, windows 8.0, windows 7
title: Windows PowerShell installeren
ms.openlocfilehash: 345cde8012bece730e7217ed16be6175ad26bb28
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429870"
---
# <a name="installing-windows-powershell"></a>Windows PowerShell installeren

Windows PowerShell is standaard in elke Windows, beginnen met Windows 7 SP1 en Windows Server 2008 R2 SP1 is geïnstalleerd.

Als u geïnteresseerd in PowerShell 6 en hoger bent, moet u PowerShell Core in plaats van Windows PowerShell installeren. Zie [PowerShell Core installeren in Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>PowerShell zoeken in Windows 10, 8.1, 8.0 en 7

Soms zoeken naar PowerShell kan ISE (Integrated Scripting Environment) in Windows-console of lastig zijn, als u de locatie van één versie van Windows worden verplaatst naar de volgende.

De volgende tabellen kunt u PowerShell niet vinden in uw Windows-versie.
Alle versies die hier zijn de oorspronkelijke versie uitgebracht, er zijn geen updates.

### <a name="for-console"></a>Voor Console

Versie | Locatie
-- | --
Windows 10 | Klik op links lagere Windows hoekpictogram en begin met het typen van PowerShell
Windows 8.1, 8.0 | Begin met het typen van PowerShell in het startscherm.<br/>Als een waarde op het bureaublad, klik op links lagere Windows hoekpictogram, begin met het typen van PowerShell
Windows 7 SP1 | Klik op links lagere hoek Windows pictogram op de zoekopdracht vak begin te typen van PowerShell

### <a name="for-ise"></a>Voor ISE

Versie | Locatie
-- | --
Windows 10 | Klik op links lagere Windows hoekpictogram en begin met het typen van ISE
Windows 8.1, 8.0 | Typ op het startscherm **PowerShell ISE**.<br/>Als u op bureaublad, klikt u op lagere hoekpictogram van Windows, typt u **PowerShell ISE**
Windows 7 SP1 | Klik op links lagere hoek Windows pictogram op de zoekopdracht vak begin te typen van PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>PowerShell zoeken in Windows Server-versies

Beginnen met Windows Server 2008 R2, worden Windows-besturingssysteem geïnstalleerd zonder de grafische gebruikersinterface (GUI).
Edities van Windows Server zonder GUI heten **Core** versies en edities met de GUI met de naam **Desktop**.

### <a name="windows-server-core-editions"></a>Windows Server Core-versies

In alle Core-versies, als u zich bij de server krijgt u een Windows-opdrachtpromptvenster.

Type `powershell` en druk op **ENTER** PowerShell starten in de opdrachtprompt-sessie.
Type `exit` de PowerShell-sessie beëindigen en terugkeren naar de opdrachtprompt.

### <a name="windows-server-desktop-editions"></a>Edities van Windows Server Desktop

In alle edities van bureaublad, klik op het pictogram links lagere hoek Windows, begin met het typen van PowerShell.
U profiteert van zowel de console en de ISE-opties.

De enige uitzondering op de regel hierboven is de ISE in Windows Server 2008 R2 SP1; in dit geval, klik op het pictogram links lagere hoek Windows, typt u PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Het controleren van de versie van PowerShell

Als wilt weten welke versie van PowerShell die u hebt geïnstalleerd, start u een PowerShell-console (of de ISE) en het type `$PSVersionTable` en druk op **ENTER**. Zoek de `PSVersion` waarde.

## <a name="upgrading-existing-windows-powershell"></a>Upgraden van bestaande Windows PowerShell

Het installatiepakket voor PowerShell wordt geleverd in een installatieprogramma WMF.
De versie van het installatieprogramma WMF overeenkomt met de versie van PowerShell; Er is geen zelfstandige installatieprogramma voor Windows PowerShell.

Als u nodig hebt om bij te werken uw huidige versie van PowerShell, in Windows, gebruikt u in de volgende tabel om te vinden van het installatieprogramma voor de versie van PowerShell die u bijwerken wilt naar.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (Zie Note1)<br/>Windows Server 2016 | - | - | - | Geïnstalleerd
Windows 8.1<br/>Windows Server 2012 R2 | - | Geïnstalleerd | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | Geïnstalleerd | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> Op de eerste release van Windows 10, met automatische updates is ingeschakeld, wordt de PowerShell van versie 5.0-5.1 bijgewerkt.
>
> Als de oorspronkelijke versie van Windows 10 niet via Windows-Updates bijgewerkt is, is de versie van PowerShell 5.0.

## <a name="need-azure-powershell"></a>Moet Azure PowerShell

Als u zoekt **Azure PowerShell**, u zou kunnen beginnen met [overzicht van Azure PowerShell](/powershell/azure/overview).

Wat u moet mogelijk anders is [installeren en configureren van Azure PowerShell](/powershell/azure/install-az-ps)

## <a name="see-also"></a>Zie ook

[Windows PowerShell-systeemvereisten](Windows-PowerShell-System-Requirements.md)

[Windows PowerShell starten](../getting-started/Starting-Windows-PowerShell.md)
