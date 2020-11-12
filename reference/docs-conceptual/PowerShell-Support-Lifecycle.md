---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Details van de beleids regels die ondersteuning bieden voor Power shell
ms.date: 11/11/2020
ms.openlocfilehash: 16b5480a0aecdd4b069d78372e09e04d1451eba6
ms.sourcegitcommit: cbbb7a804155345ccac983ccc1009ccb5e223e25
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94550278"
---
# <a name="powershell-support-lifecycle"></a>Levens cyclus van Power Shell-ondersteuning

Power shell is een afzonderlijke set hulpprogram ma's en onderdelen die los van Windows Power shell worden geleverd, geïnstalleerd en geconfigureerd. Power shell is niet opgenomen in de Windows-licentie overeenkomsten.

Power shell wordt ondersteund onder traditionele micro soft-ondersteunings overeenkomsten, waaronder [betaalde ondersteuning][], [micro soft Enter prise agreements][enterprise-agreement]en [micro soft Software Assurance][assurance]. U kunt ook betalen voor [ondersteuning][] voor Power shell door een ondersteunings aanvraag voor uw probleem te archiveren.

## <a name="community-support"></a>Community-ondersteuning

We bieden ook [Community-ondersteuning][] op github waar u een probleem, een fout of een functie aanvraag kunt indienen.
U kunt ook hulp van andere leden van de Community vinden in de micro soft [Power shell tech Community][] of een van de forums die worden vermeld in het gedeelte community van de pagina [Power shell][pshub] hub. We bieden geen garantie dat de Community tijdig het probleem zal verhelpen of oplossen. Als u een probleem ondervindt dat onmiddellijke aandacht vereist, moet u de traditionele, betaalde ondersteunings opties gebruiken.

## <a name="lifecycle-of-powershell-7"></a>Levens cyclus van Power shell 7

Met de release van Power shell 7 wordt Power shell nog steeds ondersteund onder het [beleid voor moderne levenscyclus van micro soft][modern], maar ondersteunings datums zijn gekoppeld aan [de ondersteunings levenscyclus van .net core][Long-Term]. In deze onderhouds benadering kunnen klanten LTS-releases (Long term support) of actuele releases kiezen. Power shell 7,0 is een LTS-release. Ondersteuning eindigt met de ondersteuning van .NET Core 3,1. De volgende LTS-release volgt de volgende versie van .NET core LTS. Zie de [tabel einde van Power shell-releases](#powershell-releases-end-of-life) voor de huidige laatste ondersteunings datums. LTS release-updates bevatten alleen essentiële updates en oplossingen voor beveiliging en onderhoud die zijn ontworpen om de invloed op bestaande workloads te voor komen of minimaliseren.

Een huidige release is een release die plaatsvindt tussen LTS-releases. Huidige releases kunnen essentiële oplossingen, innovaties en nieuwe functies bevatten. Een huidige release wordt drie maanden na de volgende huidige of LTS release ondersteund.

> [!IMPORTANT]
> U moet de meest recente patch update installeren om in aanmerking te komen voor ondersteuning. Als u bijvoorbeeld Power shell 7,0 en 7.0.1 hebt uitgebracht, moet u bijwerken naar 7.0.1 om in aanmerking te komen voor ondersteuning.

## <a name="supported-platforms"></a>Ondersteunde platforms

Raadpleeg de volgende tabel om te controleren of uw platform en versie van Power shell core officieel worden ondersteund.

Onze community heeft ook pakketten bijgedragen voor sommige platforms, maar ze worden niet officieel ondersteund. Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden vermeld als `Experimental` niet officieel worden ondersteund, maar zijn beschikbaar voor experimenten en feedback.

<!-- TODO: update OS list -->

|                     Platform                      |      7.0      |      7.1      |
| ------------------------------------------------- | :-----------: | :-----------: |
| Windows 8,1 en 10                               |   Ondersteund   |   Ondersteund   |
| Windows Server 2012 R2, 2016, 2019                |   Ondersteund   |   Ondersteund   |
| [Windows Server-Semi-Annual kanaal][semi-annual] |   Ondersteund   |   Ondersteund   |
| Ubuntu 16,04, 18,04                               |   Ondersteund   |   Ondersteund   |
| Ubuntu 20.04                                      | Niet ondersteund |   Ondersteund   |
| Ubuntu 19,10, 20,10 (via snap package)            |   Community   |   Ondersteund   |
| Debian 9                                          |   Ondersteund   |   Ondersteund   |
| Debian 10                                         |   Ondersteund   |   Ondersteund   |
| CentOS 7                                          |   Ondersteund   |   Ondersteund   |
| CentOS 8                                          |   Ondersteund   |   Ondersteund   |
| Red Hat Enterprise Linux 7                        |   Ondersteund   |   Ondersteund   |
| Red Hat Enterprise Linux 8                        |   Ondersteund   |   Ondersteund   |
| Fedora 31 +                                        |   Ondersteund   | Niet ondersteund |
| Alpine 3,10                                       |   Zie opmerking    | Niet ondersteund |
| Alpiene 3.11 +                                      |   Zie opmerking    |   Zie opmerking    |
| macOS 10.13 +                                      |   Ondersteund   |   Ondersteund   |
| Arch                                              |   Community   |   Community   |
| Raspbian                                          |   Community   |   Community   |
| Kali                                              |   Community   |   Community   |
| AppImage (werkt op meerdere Linux-platforms)      |   Community   |   Community   |
| [Snap-pakket](https://snapcraft.io/powershell)   |   Zie opmerking    |   Zie opmerking    |

> [!NOTE]
> Snap-pakketten worden hetzelfde ondersteund als de distributie waarmee u het pakket uitvoert.

> [!NOTE]
> CIM, externe communicatie van Power shell en DSC worden niet ondersteund in Alpine.

## <a name="powershell-releases-end-of-life"></a>Release van Power shell is geëindigd

Op basis van de [levens cyclus van Power shell](#lifecycle-of-powershell-7), worden in de volgende tabel de datums weer gegeven wanneer verschillende releases niet meer worden ondersteund.

| Versie |          Einde van de levens duur           |
| :-----: | ------------------------------ |
|   7.1   | medio februari 2022 (geprojecteerd) |
|   7.0   | 3 december 2022               |
|   6,2   | 4 september 2020              |
|   6.1   | 28 september 2019             |
|   6.0   | 13 februari 2019              |

> [!NOTE]
> Dit document bevat ondersteuning voor Power shell core. Windows Power shell (1,0-5,1) is een onderdeel van het Windows-besturings systeem. Onderdelen ontvangen dezelfde ondersteuning als het bovenliggende product of platform. Zie [informatie over de levens cyclus van producten en services](/lifecycle/products/)voor meer informatie.

## <a name="unsupported-platforms"></a>Niet-ondersteunde platforms

Wanneer een platform versie het einde van de levens duur bereikt zoals gedefinieerd door de platform eigenaar, zal Power shell core ook niet langer ondersteuning bieden voor die platform versie. Eerder vrijgegeven pakketten blijven beschikbaar voor klanten die toegang nodig hebben, maar formele ondersteuning en updates van welke aard dan ook niet meer.

De distributie-eigen aren hebben daarom de volgende versies gestopt en worden niet ondersteund.

<!-- TODO: Update this table Jason-->

|    Platform    | Versie |                                                         Einde van de levens duur                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [Augustus 2017](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [december 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Mei 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42,1   | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42,2   | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42,3   | [Juli 2019](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14,04  | [April 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16,10  | [Juli 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17,04  | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17,10  | [Juli 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Januari 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Januari 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Opmerkingen over licenties

Power shell core wordt uitgebracht onder de [MIT-licentie][]. Onder deze licentie en zonder een betaalde ondersteunings overeenkomst zijn gebruikers beperkt tot [ondersteuning][]van de community. Met ondersteuning van de Community biedt micro soft geen garanties voor reactie tijd of oplossingen.

## <a name="windows-powershell-compatibility"></a>Compatibiliteit met Windows Power shell

De ondersteunings levenscyclus voor Power Shell heeft geen betrekking op modules die buiten het Power shell-release pakket worden verzonden. Het gebruik `ActiveDirectory` van de module die wordt geleverd als onderdeel van Windows Server wordt bijvoorbeeld ondersteund onder de [levens cyclus van Windows-ondersteuning][].

Power shell 7 verbetert de compatibiliteit met bestaande Power shell-modules die zijn geschreven voor Windows Power shell.
Zie het [about_Windows_Compatibility][] -artikel en de [lijst met compatibiliteits modules][]voor meer informatie.

> [!NOTE]
> De [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) -module is niet meer nodig in Power shell 7 en wordt niet ondersteund.

## <a name="experimental-features"></a>Experimentele functies

[Experimentele functies][] zijn beperkt tot [ondersteuning](#community-support)van de community.

## <a name="security-servicing-criteria"></a>Criteria voor beveiligings onderhoud

Power shell volgt de [micro soft security Servicing criteria voor Windows][].
De onderstaande tabel bevat een overzicht van de functies die voldoen aan de onderhouds criteria en die niet.

| Functie                          | Type             |
|----------------------------------|------------------|
| Uitvoerings beleid                 | Diep ingrijpende verdediging |
| Systeem vergrendeling-met AppLocker | Diep ingrijpende verdediging |
| Systeem Lockdown-met WDAC      | Beveiligings functie |

## <a name="release-history"></a>Release geschiedenis

De volgende tabel bevat een tijd lijn van de belangrijkste releases van Power shell. Deze tabel wordt vermeld voor historische Naslag informatie. Het is niet bedoeld voor gebruik om de ondersteunings levenscyclus te bepalen.

|         Versie          | Releasedatum |                                                                     Notitie                                                                      |
| ------------------------ | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Power shell 7,1 (actueel) |   Nov-2020   | Gebouwd op .NET Core 5,0 (actueel)                                                                                                              |
| Power shell 7,0 (LTS)     |   Mrt-2020   | Gebouwd op .NET Core 3,1 (LTS)                                                                                                                  |
| Power shell 6,0           |   Jan-2018   | First release, gebouwd op .NET Core 2,1. Installeerbaar op Windows, Linux en macOS.                                                              |
| PowerShell 5.1           |   Aug-2016   | Uitgebracht in Windows 10 jubileum update en Windows Server 2016                                                                             |
| PowerShell 5.0           |   Feb-2016   | Uitgebracht in Windows Management Framework (WMF) 5,0                                                                                            |
| PowerShell 4.0           |   Okt-2013   | Geïntegreerd in Windows 8,1 en met Windows Server 2012 R2. Installeerbaar op Windows 7 SP1, Windows Server 2008 R2 SP1 en Windows Server 2012. |
| PowerShell 3.0           |   Okt-2012   | Geïntegreerd in Windows 8 en Windows Server 2012. Installeerbaar op Windows 7 SP1, Windows Server 2008 SP1 en Windows Server 2008 R2 SP1.  |
| Power Shell 2,0           |   Jul-2009   | Geïntegreerd in Windows 7 en Windows Server 2008 R2. Installeerbaar op Windows XP SP3, Windows Server 2003 SP2 en Windows Vista SP1.            |
| Power shell 1,0           |   Nov-2006   | Installeerbaar op Windows XP SP2, Windows Server 2003 SP1 en Windows Vista. Optioneel onderdeel van Windows Server 2008.                          |

<!-- hyperlink references -->
[betaalde ondersteuning]: https://support.microsoft.com/hub/4343728/support-for-business
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[Community-ondersteuning]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning voor assistentie]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT-licentie]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Windows-ondersteunings levenscyclus]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[lijst met compatibiliteits modules]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Experimentele functies]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
[Micro soft security-onderhouds criteria voor Windows]: https://www.microsoft.com/msrc/windows-security-servicing-criteria
