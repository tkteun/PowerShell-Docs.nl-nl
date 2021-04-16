---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Details van de beleidsregels voor ondersteuning voor PowerShell
ms.date: 11/11/2020
ms.openlocfilehash: 4f1b0a2b39f19a59a550b53a47f7e8cbbe937297
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543998"
---
# <a name="powershell-support-lifecycle"></a>Levenscyclus van PowerShell-ondersteuning

PowerShell is een afzonderlijke set hulpprogramma's en onderdelen die afzonderlijk wordt verzonden, geïnstalleerd en geconfigureerd Windows PowerShell. PowerShell is niet opgenomen in de Windows-licentieovereenkomsten.

PowerShell wordt ondersteund onder traditionele Microsoft-ondersteuningsovereenkomsten, waaronder betaalde [ondersteuning,][] [Microsoft Enterprise Agreements][enterprise-agreement]en Microsoft [Software Assurance.][assurance] U kunt ook betalen voor [ondersteuning voor][] PowerShell door een ondersteuningsaanvraag in te dienen voor uw probleem.

## <a name="community-support"></a>Ondersteuning van de community

We bieden ook [ondersteuning van de community][] op GitHub, waar u een probleem, fout of functieaanvraag kunt indienen.
U kunt ook hulp krijgen van andere leden van de community in de Microsoft [PowerShell Tech Community][] of een van de forums die worden vermeld in de communitysectie van de [PowerShell][pshub] Hub-pagina. We bieden geen garantie dat de community uw probleem tijdig zal oplossen of oplossen. Als u een probleem hebt dat onmiddellijke aandacht vereist, moet u de traditionele, betaalde ondersteuningsopties gebruiken.

## <a name="lifecycle-of-powershell-7"></a>Levenscyclus van PowerShell 7

Met de release van PowerShell 7 wordt PowerShell nog steeds ondersteund onder het [Microsoft Modern Lifecycle Policy,][modern]maar ondersteuningsdatums zijn gekoppeld aan de ondersteuningslevenscyclus van [.NET Core.][Long-Term] Bij deze onderhoudsbenadering kunnen klanten kiezen voor LTS-releases (Long Term Support) of Current releases. PowerShell 7.0 is een LTS-release. Ondersteuning eindigt met de ondersteuning van .NET Core 3.1. De volgende LTS-release volgt de volgende .NET Core LTS-release. Zie de [tabel Einde levensduur van PowerShell-releases voor](#powershell-releases-end-of-life) de huidige einddatums voor ondersteuning. LTS-release-updates bevatten alleen essentiële beveiligings- en onderhoudsupdates en -oplossingen die zijn ontworpen om de impact op bestaande workloads te voorkomen of te minimaliseren.

Een Huidige release is een release die plaatsvindt tussen LTS-releases. Huidige releases kunnen kritieke oplossingen, innovaties en nieuwe functies bevatten. Een huidige release wordt drie maanden na de volgende Current- of LTS-release ondersteund.

> [!IMPORTANT]
> U moet de nieuwste patchupdate hebben geïnstalleerd om in aanmerking te komen voor ondersteuning. Als u bijvoorbeeld PowerShell 7.0 en 7.0.1 gebruikt, moet u bijwerken naar 7.0.1 om in aanmerking te komen voor ondersteuning.

## <a name="supported-platforms"></a>Ondersteunde platforms

Als u wilt controleren of uw platform en versie van PowerShell Core officieel worden ondersteund, bekijkt u de volgende tabel.

Onze community heeft ook pakketten bijgedragen voor sommige platforms, maar ze worden niet officieel ondersteund. Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden vermeld `Experimental` als worden niet officieel ondersteund, maar zijn beschikbaar voor experimenten en feedback.

<!-- TODO: update OS list -->

|                     Platform                      |      7.0      |      7.1      |
| ------------------------------------------------- | :-----------: | :-----------: |
| Windows 8.1 en 10                               |   Ondersteund   |   Ondersteund   |
| Windows Server 2012 R2, 2016, 2019                |   Ondersteund   |   Ondersteund   |
| [Windows Server Semi-Annual-kanaal][semi-annual] |   Ondersteund   |   Ondersteund   |
| Ubuntu 16.04, 18.04                               |   Ondersteund   |   Ondersteund   |
| Ubuntu 20.04                                      | Niet ondersteund |   Ondersteund   |
| Ubuntu 19.10, 20.10 (via Snap Package)            |   Community   |   Ondersteund   |
| Debian 9                                          |   Ondersteund   |   Ondersteund   |
| Debian 10                                         |   Ondersteund   |   Ondersteund   |
| CentOS 7                                          |   Ondersteund   |   Ondersteund   |
| CentOS 8                                          |   Ondersteund   |   Ondersteund   |
| Red Hat Enterprise Linux 7                        |   Ondersteund   |   Ondersteund   |
| Red Hat Enterprise Linux 8                        |   Ondersteund   |   Ondersteund   |
| Fedora 31+                                        |   Ondersteund   | Niet ondersteund |
| Alpine 3.10                                       |   Zie Opmerking 1  | Niet ondersteund |
| Alpine 3.11+                                      |   Zie Opmerking 1  |   Zie Opmerking 1  |
| macOS 10.13+                                      |   Ondersteund   |   Ondersteund   |
| Arch                                              |   Community   |   Community   |
| Raspbian                                          |   Community   |   Community   |
| Kali                                              |   Community   |   Community   |
| AppImage (werkt op meerdere Linux-platforms)      |   Community   |   Community   |
| [Pakket uitlijnen](https://snapcraft.io/powershell)   |   Zie opmerking 2  |   Zie opmerking    |

> [!NOTE]
> - 1: CIM, PowerShell voor remoting en DSC worden niet ondersteund in Alpine.
> - 2 - Snap-pakketten worden op dezelfde manier ondersteund als de distributie waar u het pakket op wilt uitvoeren.

## <a name="powershell-releases-end-of-life"></a>Einde levensduur van PowerShell-releases

Op basis van [de levenscyclus van PowerShell](#lifecycle-of-powershell-7)worden in de volgende tabel de datums vermeld waarop verschillende releases niet meer worden ondersteund.

| Versie |          Einde van de levensduur           |
| :-----: | ------------------------------ |
|   7.1   | half februari 2022 (geprojecteerd) |
|   7.0   | 3 december 2022               |
|   6,2   | 4 september 2020              |
|   6.1   | 28 september 2019             |
|   6.0   | 13 februari 2019              |

> [!NOTE]
> Dit document gaat over ondersteuning voor PowerShell Core. Windows PowerShell (1.0 - 5.1) is een onderdeel van het Windows-besturingssysteem. Onderdelen krijgen dezelfde ondersteuning als het bovenliggende product of platform. Zie Product [and Services Lifecycle Information (Levenscyclusinformatie voor producten en services) voor meer informatie.](/lifecycle/products/)

## <a name="unsupported-platforms"></a>Niet-ondersteunde platforms

Wanneer een platformversie het einde van de levensduur bereikt, zoals gedefinieerd door de platformeigenaar, PowerShell Core deze platformversie ook niet meer ondersteund. Eerder uitgebrachte pakketten blijven beschikbaar voor klanten die toegang nodig hebben, maar formele ondersteuning en updates van welke aard dan ook, worden niet meer verstrekt.

De distributie-eigenaren hebben daarom de ondersteuning voor de volgende versies beëindigd en worden niet ondersteund.

<!-- TODO: Update this table Jason-->

|    Platform    | Versie |                                                         Einde van de levensduur                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [Augustus 2017](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Mei 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42.2   | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42.3   | [Juli 2019](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [April 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16,10  | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.10  | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Januari 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Januari 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Opmerkingen over licentieverlening

PowerShell Core wordt vrijgegeven onder de [MIT-licentie][]. Onder deze licentie en zonder een betaalde ondersteuningsovereenkomst zijn gebruikers beperkt tot [ondersteuning van de community.][] Met ondersteuning van de community garandeert Microsoft geen reactiesnelheid of oplossingen.

## <a name="windows-powershell-compatibility"></a>Windows PowerShell compatibiliteit

De ondersteuningslevenscyclus voor PowerShell heeft geen betrekking op modules die worden aangeboden buiten het Release-pakket van PowerShell 7. Het gebruik van de module die wordt geleverd als onderdeel van Windows Server wordt bijvoorbeeld `ActiveDirectory` ondersteund onder de Levenscyclus van [Windows-ondersteuning.][]

PowerShell 7 verbetert de compatibiliteit met bestaande PowerShell-modules die zijn geschreven voor Windows PowerShell.
Zie het artikel about_Windows_Compatibility en [de][] [modulecompatibiliteitslijst voor meer informatie.][]

> [!NOTE]
> De [**module WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) is niet meer nodig in PowerShell 7 en wordt niet ondersteund.

## <a name="experimental-features"></a>Experimentele functies

[Experimentele functies zijn][] beperkt tot [ondersteuning van de community.](#community-support)

## <a name="security-servicing-criteria"></a>Criteria voor beveiligingsservice

PowerShell volgt de [Microsoft Security Servicing Criteria voor Windows.][]
De onderstaande tabel bevat een overzicht van de functies die voldoen aan de onderhoudscriteria en de functies die dat niet doen.

|                  Functie                   |       Type       |
| ------------------------------------------ | ---------------- |
| Systeemvergrendeling - met WDAC                | Beveiligingsfunctie |
| Beperkte taalmodus - met WDAC      | Beveiligingsfunctie |
| Systeemvergrendeling - met AppLocker           | Diepgaande verdediging |
| Beperkte taalmodus - met AppLocker | Diepgaande verdediging |
| Uitvoeringsbeleid                           | Diepgaande verdediging |

> [!NOTE]
> Er is een hoekscenario in AppLocker  waarin u alleen regels voor weigeren hebt en de beperkte taalmodus niet wordt gebruikt om het beleid af te dwingen waarmee u het uitvoeringsbeleid kunt omzeilen.
> Vanaf PowerShell 7.2 is er een wijziging aangebracht om ervoor te zorgen dat AppLocker-regels voorrang krijgen op een `Set-ExecutionPolicy -ExecutionPolicy Bypass` opdracht.

Zie Application Controls for Windows (Toepassingsbesturingselementen voor [Windows)](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)voor meer informatie over AppLocker en Windows Defender Application Control (WDAC).

## <a name="release-history"></a>Releasegeschiedenis

De volgende tabel bevat een tijdlijn van de belangrijkste releases van PowerShell. Deze tabel is beschikbaar voor historische naslag. Het is niet bedoeld voor gebruik om de ondersteuningslevenscyclus te bepalen.

|         Versie          | Releasedatum |                                                                     Notitie                                                                      |
| ------------------------ | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.1 (actueel) |   November 2020   | Gebouwd op .NET 5.0 (actueel).                                                                                                                  |
| PowerShell 7.0 (LTS)     |   Maart 2020   | Gebouwd op .NET Core 3.1 (LTS).                                                                                                                 |
| PowerShell 6.2           |   Maart 2019   |                                                                                                                                               |
| PowerShell 6.1           |   Sep-2018   | Gebouwd op .NET Core 2.1.                                                                                                                       |
| PowerShell 6.0           |   Jan-2018   | Eerste versie, gebouwd op .NET Core 2.0. Kan worden geïnstalleerd in Windows, Linux en macOS.                                                              |
| PowerShell 5.1           |   Aug-2016   | Uitgebracht in Windows 10 Jubileumupdate en Windows Server 2016.                                                                            |
| PowerShell 5.0           |   Feb-2016   | Uitgebracht in Windows Management Framework (WMF) 5.0.                                                                                           |
| PowerShell 4.0           |   Okt-2013   | Geïntegreerd in Windows 8.1 en met Windows Server 2012 R2. Kan worden geïnstalleerd op Windows 7 SP1, Windows Server 2008 R2 SP1 en Windows Server 2012. |
| PowerShell 3.0           |   Okt-2012   | Geïntegreerd in Windows 8 en met Windows Server 2012. Kan worden geïnstalleerd op Windows 7 SP1, Windows Server 2008 SP1 en Windows Server 2008 R2 SP1.  |
| PowerShell 2.0           |   Jul-2009   | Geïntegreerd in Windows 7 en Windows Server 2008 R2. Kan worden geïnstalleerd op Windows XP SP3, Windows Server 2003 SP2 en Windows Vista SP1.            |
| PowerShell 1.0           |   November 2006   | Kan worden geïnstalleerd op Windows XP SP2, Windows Server 2003 SP1 en Windows Vista. Optioneel onderdeel van Windows Server 2008.                          |

<!-- hyperlink references -->
[betaalde ondersteuning]: https://support.microsoft.com/hub/4343728/support-for-business
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[ondersteuning van de community]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteunde ondersteuning]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Levenscyclus van Windows-ondersteuning]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[compatibiliteitslijst voor modules]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentele functies]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
[Microsoft Security Servicing Criteria for Windows]: https://www.microsoft.com/msrc/windows-security-servicing-criteria
