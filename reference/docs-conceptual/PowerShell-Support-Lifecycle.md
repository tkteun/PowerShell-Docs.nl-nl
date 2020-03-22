---
title: Levenscyclus voor ondersteuning van PowerShell Core
description: Beleids regels die ondersteuning bieden voor Power shell core
ms.date: 03/09/2020
ms.openlocfilehash: c1e91aa193dd4a6353098e16ae18301c0753ea85
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082408"
---
# <a name="powershell-support-lifecycle"></a>Levens cyclus van Power Shell-ondersteuning

Power shell is een afzonderlijke set hulpprogram ma's en onderdelen die los van Windows Power shell worden geleverd, geïnstalleerd en geconfigureerd. Power shell is niet opgenomen in de Windows-licentie overeenkomsten.

Power shell wordt ondersteund onder traditionele micro soft-ondersteunings overeenkomsten, waaronder [premier][], [micro soft Enter prise agreements][enterprise-agreement]en [micro soft Software Assurance][assurance].
U kunt ook betalen voor [ondersteuning][] voor Power shell door een ondersteunings aanvraag voor uw probleem te archiveren.

## <a name="community-support"></a>Community-ondersteuning

We bieden ook [Community-ondersteuning][] op github waar u een probleem, een fout of een functie aanvraag kunt indienen.
U kunt ook hulp van andere leden van de Community vinden in de micro soft [Technische community van Power shell][] of een van de forums die worden vermeld in het gedeelte community van de pagina [Power shell][pshub] hub. We bieden geen garantie dat de Community tijdig het probleem zal verhelpen of oplossen. Als u een probleem ondervindt dat onmiddellijke aandacht vereist, moet u de traditionele, betaalde ondersteunings opties gebruiken.

## <a name="lifecycle-of-powershell-7"></a>Levens cyclus van Power shell 7

Met de release van Power shell 7 wordt Power shell nog steeds ondersteund onder het [beleid voor moderne levenscyclus van micro soft][modern], maar ondersteunings datums zijn gekoppeld aan [de ondersteunings levenscyclus van .net core][Long-Term]. In deze onderhouds benadering kunnen klanten LTS-releases (Long term support) of actuele releases kiezen. Power shell 7,0 is een LTS-release. Ondersteuning eindigt met de ondersteuning van .NET Core 3,1. De volgende LTS-release volgt de volgende versie van .NET core LTS. Zie de [tabel einde van Power shell-releases](#powershell-releases-end-of-life) voor huidige laatste ondersteunings datums. LTS release-updates bevatten alleen essentiële updates en oplossingen voor beveiliging en onderhoud die zijn ontworpen om de invloed op bestaande workloads te voor komen of minimaliseren.

Een huidige release is een release die plaatsvindt tussen LTS-releases. Huidige releases kunnen essentiële oplossingen, innovaties en nieuwe functies bevatten. Een huidige release wordt drie maanden na de volgende huidige of LTS release ondersteund.

> [!IMPORTANT]
> U moet de meest recente patch update installeren om in aanmerking te komen voor ondersteuning. Als u bijvoorbeeld Power shell 7,0 en 7.0.1 hebt uitgebracht, moet u bijwerken naar 7.0.1 om in aanmerking te komen voor ondersteuning.

## <a name="lifecycle-of-powershell-core-6x"></a>Levens cyclus van Power shell Core 6. x

Power shell Core heeft het [micro soft moderne levenscyclus beleid][modern]gebruikt. Deze ondersteunings levenscyclus is bedoeld om klanten up-to-date te houden met de meest recente versies.

De vertakking versie 6. x van Power shell Core is ongeveer eenmaal per zes maanden bijgewerkt (bijvoorbeeld: 6,0, 6,1, 6,2, etc.). Met de release van Power shell 7 zijn er echter geen kleine versies van 6. x meer beschikbaar. Power shell 6.2. x blijft onderhouds updates ontvangen en wordt nog steeds ondersteund.

> [!IMPORTANT]
> U moet binnen zes maanden na de release van elke nieuwe secundaire versie een update voor het ontvangen van ondersteuning door lopen.

Als Power shell Core 6,1 bijvoorbeeld is uitgebracht op 1 juli 2018, wordt u naar verwachting naar Power shell Core 6,1 bijgewerkt op 1 januari 2019 om ondersteuning te onderhouden.

> [!IMPORTANT]
> U moet binnen 30 dagen na elke nieuwe versie van de patch een update uitvoeren om ondersteuning te blijven ontvangen.

Als u bijvoorbeeld Power shell Core 6,1 uitvoert en 6.1.3 is uitgebracht op 19 februari 2019, zou u op 21 maart 2019 naar verwachting moeten bijwerken naar Power shell Core 6.1.3. Dit is 30 dagen na de release voor het onderhouden van de ondersteuning. Als er oplossingen worden gevonden die vereist zijn, worden de oplossingen vrijgegeven in de volgende cumulatieve update.

Voor het beleid voor moderne levens cyclus moet micro soft klanten 12 maanden vertellen voordat de ondersteuning voor een product (dat wil zeggen Power shell core) wordt beëindigd.

## <a name="supported-platforms"></a>Ondersteunde platforms

Raadpleeg de volgende tabel om te controleren of uw platform en versie van Power shell core officieel worden ondersteund.

Onze community heeft ook pakketten bijgedragen voor sommige platforms, maar ze worden niet officieel ondersteund. Deze pakketten zijn gemarkeerd als `Community` in de tabel.

Platforms die worden vermeld als `Experimental`, worden niet officieel ondersteund, maar zijn beschikbaar voor experimenteren en feedback.

| Platform                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8,1 en 10                               |   Ondersteund   | Ondersteund |
| Windows Server 2012 R2, 2016                      |   Ondersteund   | Ondersteund |
| [Windows Server Semi-Annual-kanaal][semi-annual] |   Ondersteund   | Ondersteund |
| Ubuntu 16,04 en 18,04                            |   Ondersteund   | Ondersteund |
| Ubuntu 19,10 (via snap package)                   |   Community   | Community |
| Ubuntu 20,04 (via snap package)                   |   Community   | Community |
| Debian 9                                          |   Ondersteund   | Ondersteund |
| Debian 10                                         | Niet ondersteund | Ondersteund |
| CentOS 7                                          |   Ondersteund   | Ondersteund |
| CentOS 8                                          | Niet ondersteund | Ondersteund |
| Red Hat Enterprise Linux 7                        |   Ondersteund   | Ondersteund |
| Red Hat Enterprise Linux 8                        | Niet ondersteund | Ondersteund |
| Fedora 30                                         | Niet ondersteund | Ondersteund |
| Alpine 3,8                                        |   Zie opmerking    | Zie opmerking  |
| Alpine 3,9 en 3,10                               | Niet ondersteund | Zie opmerking  |
| macOS 10.12+                                      |   Ondersteund   | Ondersteund |
| Arch                                              |   Community   | Community |
| Raspbian                                          |   Community   | Community |
| Kali                                              |   Community   | Community |
| AppImage (werkt op meerdere Linux-platforms)      |   Community   | Community |
| [Snap-pakket](https://snapcraft.io/powershell)   |   Zie opmerking    | Zie opmerking  |

> [!NOTE]
> Snap-pakketten worden hetzelfde ondersteund als de distributie waarmee u het pakket uitvoert.

> [!NOTE]
> CIM, externe communicatie van Power shell en DSC worden niet ondersteund in Alpine.

## <a name="powershell-releases-end-of-life"></a>Release van Power shell is geëindigd

Op basis van de [levens cyclus van Power shell](#lifecycle-of-powershell-7), worden in de volgende tabel de datums weer gegeven wanneer verschillende releases niet meer worden ondersteund.

| Version |    Einde van de levens duur     |
| :-----: | ------------------ |
|   7.0   | 3 december 2022   |
|   6.2   | 4 september 2020  |
|   6.1   | 28 september 2019 |
|   6.0   | 13 februari 2019  |

## <a name="unsupported-platforms"></a>Niet-ondersteunde platforms

Wanneer een platform versie het einde van de levens duur bereikt zoals gedefinieerd door de platform eigenaar, zal Power shell core ook niet langer ondersteuning bieden voor die platform versie. Eerder vrijgegeven pakketten blijven beschikbaar voor klanten die toegang nodig hebben, maar formele ondersteuning en updates van welke aard dan ook niet meer.

De distributie-eigen aren hebben daarom de volgende versies gestopt en worden niet ondersteund.

|    Platform    | Version |                                                         Einde van de levens duur                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [Juni 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [2017 augustus](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [December 2017](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [Mei 2018](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [November 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [Mei 2019](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [Mei 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42,2   | [Januari 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42,3   | [2019 juli](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [April 2019](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16,10  | [2017 juli](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17,04  | [Januari 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17,10  | [2018 juli](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [Januari 2020](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [Januari 2020](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>Opmerkingen over licenties

Power shell core wordt uitgebracht onder de [MIT-licentie][]. Onder deze licentie en zonder een betaalde ondersteunings overeenkomst zijn gebruikers beperkt tot [Community-ondersteuning][]van de community. Met ondersteuning van de Community biedt micro soft geen garanties voor reactie tijd of oplossingen.

## <a name="windows-powershell-compatibility"></a>Compatibiliteit met Windows Power shell

De ondersteunings levenscyclus voor Power Shell heeft geen betrekking op modules die buiten het Power shell-release pakket worden verzonden. Het gebruik van de `ActiveDirectory`-module die wordt geleverd als onderdeel van Windows Server wordt bijvoorbeeld ondersteund onder de [Windows-ondersteunings levenscyclus][].

Power shell 7 verbetert de compatibiliteit met bestaande Power shell-modules die zijn geschreven voor Windows Power shell.
Zie het [about_Windows_Compatibility][] -artikel en de [lijst met compatibiliteits modules][]voor meer informatie.

> [!NOTE]
> De [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) -module is niet meer nodig in Power shell 7 en wordt niet ondersteund.

## <a name="experimental-features"></a>Experimentele functies

[Experimentele functies][] zijn beperkt tot [ondersteuning](#community-support)van de community.

## <a name="release-history"></a>Release geschiedenis

De volgende tabel bevat een tijd lijn van de belangrijkste releases van Power shell. Deze tabel wordt vermeld voor historische Naslag informatie. Het is niet bedoeld voor gebruik om de ondersteunings levenscyclus te bepalen.

|       Version        | Releasedatum |                                                                     Opmerking                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Power shell 7,0 (LTS) |   Mrt-2020   | Gebouwd op .NET Core 3,1 (LTS)                                                                                                                  |
| Power shell 6,0       |   Jan-2018   | First release, gebouwd op .NET Core 2,1. Installeerbaar op Windows, Linux en macOS.                                                              |
| PowerShell 5.1       |   Aug-2016   | Uitgebracht in Windows 10 jubileum update en Windows Server 2016                                                                             |
| Power shell 5,0       |   Feb-2016   | Uitgebracht in Windows Management Framework (WMF) 5,0                                                                                            |
| Power Shell 4,0       |   Okt-2013   | Geïntegreerd in Windows 8,1 en met Windows Server 2012 R2. Installeerbaar op Windows 7 SP1, Windows Server 2008 R2 SP1 en Windows Server 2012. |
| Power Shell 3,0       |   Okt-2012   | Geïntegreerd in Windows 8 en Windows Server 2012. Installeerbaar op Windows 7 SP1, Windows Server 2008 SP1 en Windows Server 2008 R2 SP1.  |
| Power Shell 2,0       |   Jul-2009   | Geïntegreerd in Windows 7 en Windows Server 2008 R2. Installeerbaar op Windows XP SP3, Windows Server 2003 SP2 en Windows Vista SP1.            |
| Power shell 1,0       |   Nov-2006   | Installeerbaar op Windows XP SP2, Windows Server 2003 SP1 en Windows Vista. Optioneel onderdeel van Windows Server 2008.                          |

<!-- hyperlink references -->
[Premier]: https://www.microsoft.com/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[Community-ondersteuning]: /powershell/scripting/community/community-support
[pshub]: /powershell
[Technische community van Power shell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[ondersteuning]: https://support.microsoft.com/assistedsupportproducts
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
